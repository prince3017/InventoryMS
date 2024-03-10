1. Explain the relationship between the "Product" and "Product_Category" entities from the above diagram.

Ans:  The relationship between the "Product" and "Product_Category" entities in the given database schema is a one-to-many relationship, also known as a parent-child relationship.
      In this relationship, each product belongs to a single product category, but a product category can have multiple products associated with it.
      Here's how the relationship is defined:
          1. In the "Product" entity, there is a column named "category_id" of data type "int". This column serves as a foreign key 
              reference to the primary key ("id" column) of the "Product_Category" entity.
          2. The "category_id" column in the "Product" entity establishes the connection between a specific product and its corresponding product category.
          3. A product can have only one value for "category_id", which means that a product can belong to only one product category.
          4. However, multiple products can have the same "category_id" value, indicating that multiple products can belong to the same product category.
      Example: let's say we have a product category with the id "1" and name "Electronics".
      We can have multiple products like "Laptop", "Smartphone", "Tablet", etc., all belonging to the "Electronics" category by having their "category_id" set to "1".

2. How could you ensure that each product in the "Product" table has a valid category assigned to it?

Ans:  To ensure that each product in the "Product" table has a valid category assigned to it, you can leverage the foreign key constraint provided by relational database management systems (RDBMS).
      Here's how you can implement this constraint:
        1. In the product table schema, define the category_id column as a foreign key that references the id column of the product_category table.
        2. ## CREATE TABLE product (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    `desc` TEXT,
    SKU VARCHAR(255) NOT NULL,
    category_id INT NOT NULL,
    inventory_id INT NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    discount_id INT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    deleted_at TIMESTAMP NULL,
    FOREIGN KEY (category_id) REFERENCES product_category(id),
    FOREIGN KEY (inventory_id) REFERENCES product_inventory(id),
    FOREIGN KEY (discount_id) REFERENCES discount(id)
);
