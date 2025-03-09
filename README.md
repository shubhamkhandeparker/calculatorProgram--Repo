This is a simple code where i crated a calculator using java.
My plan is to make this code as EMI calculator .
Author - Shubham Khandeparker.

Here i have written Entire Code Detail using Chat GPT 

//Code Details 

Here's a step-by-step breakdown of your Java Calculator program. You can use this to document the code in your `README.md` file on GitHub.

---

# **Calculator Application (Java Swing)**

This is a simple **calculator application** built using **Java Swing**. It supports basic arithmetic operations like **addition, subtraction, multiplication, and division**, along with other functionalities such as **clear, delete, negative number conversion, and decimal input**.

---

## **Features**
- GUI-based calculator using `JFrame`, `JPanel`, and `JButton`.
- Supports `+`, `-`, `*`, `/`, `.` (decimal).
- Delete button to remove the last digit.
- Clear button to reset the calculator.
- Negative button to toggle positive/negative numbers.

---

## **Code Breakdown**

### **1. Import Required Libraries**
```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
```
- `javax.swing.*` → Used for GUI components like buttons, panels, and text fields.
- `java.awt.*` → Used for layout and styling.
- `java.awt.event.*` → Used for event handling (button clicks).

---

### **2. Create the Main Class and Implement ActionListener**
```java
public class Main implements ActionListener {
```
- `Main` class implements `ActionListener` to handle button click events.

---

### **3. Declare GUI Components**
```java
JFrame frame;
JTextField textField;
JButton[] numberButtons = new JButton[10];
JButton[] functionButtons = new JButton[9];
JButton addButton, subButton, mulButton, divButton;
JButton decButton, equButton, delButton, clrButton, negButton;
JPanel panel;
```
- `JFrame` → Main application window.
- `JTextField` → Displays input and results.
- `JButton` → Number and function buttons.
- `JPanel` → Holds number and function buttons in a grid layout.

---

### **4. Define Variables**
```java
Font myFont = new Font("Arial", Font.BOLD, 30);
double num1 = 0, num2 = 0, result = 0;
char operator;
```
- **Font**: Sets text style and size.
- **Variables**: Store first number (`num1`), second number (`num2`), and the `result`.
- **Operator**: Stores the selected mathematical operator.

---

### **5. Constructor - Initialize GUI Components**
```java
frame = new JFrame("Calculator");
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
frame.setSize(420, 550);
frame.setLayout(null);
```
- Creates the **main window** of size **420x550** pixels.
- `setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE)` ensures the program exits when the window is closed.
- `setLayout(null)` disables default layout for manual positioning.

#### **Initialize Text Field**
```java
textField = new JTextField();
textField.setBounds(50, 25, 300, 50);
textField.setFont(myFont);
textField.setEnabled(false);
```
- Displays input/output values.
- **Disabled** so users can't type manually.

---

### **6. Create Buttons**
#### **Function Buttons**
```java
addButton = new JButton("+");
subButton = new JButton("-");
mulButton = new JButton("*");
divButton = new JButton("/");
decButton = new JButton(".");
equButton = new JButton("=");
delButton = new JButton("Delete");
clrButton = new JButton("Clear");
negButton = new JButton("(-)");
```
- Buttons for arithmetic operations, decimal, equal, delete, and clear.

#### **Store Function Buttons in an Array**
```java
functionButtons[0] = addButton;
functionButtons[1] = subButton;
functionButtons[2] = mulButton;
functionButtons[3] = divButton;
functionButtons[4] = decButton;
functionButtons[5] = equButton;
functionButtons[6] = delButton;
functionButtons[7] = clrButton;
functionButtons[8] = negButton;
```
- **Easier to manage function buttons** using an array.

#### **Add Action Listener and Styling**
```java
for (int i = 0; i < 9; i++) {
    functionButtons[i].addActionListener(this);
    functionButtons[i].setFont(myFont);
    functionButtons[i].setFocusable(false);
}
```
- Assigns action listeners to detect button clicks.
- Applies consistent font style.

#### **Create Number Buttons**
```java
for (int i = 0; i < 10; i++) {
    numberButtons[i] = new JButton(String.valueOf(i));
    numberButtons[i].addActionListener(this);
    numberButtons[i].setFont(myFont);
    numberButtons[i].setFocusable(false);
}
```
- Loops through **0-9** and creates number buttons dynamically.

---

### **7. Position Special Buttons**
```java
negButton.setBounds(50, 430, 100, 50);
delButton.setBounds(150, 430, 100, 50);
clrButton.setBounds(250, 430, 100, 50);
```
- Positions `Negative`, `Delete`, and `Clear` buttons at the bottom.

---

### **8. Create Button Panel**
```java
panel = new JPanel();
panel.setBounds(50, 100, 300, 300);
panel.setLayout(new GridLayout(4, 4, 10, 10));
```
- Uses a **4x4 grid** layout to align buttons.
- Adds a **10-pixel gap** between buttons.

#### **Add Buttons to Panel**
```java
panel.add(numberButtons[1]);
panel.add(numberButtons[2]);
panel.add(numberButtons[3]);
panel.add(addButton);

panel.add(numberButtons[4]);
panel.add(numberButtons[5]);
panel.add(numberButtons[6]);
panel.add(subButton);

panel.add(numberButtons[7]);
panel.add(numberButtons[8]);
panel.add(numberButtons[9]);
panel.add(mulButton);

panel.add(decButton);
panel.add(numberButtons[0]);
panel.add(equButton);
panel.add(divButton);
```
- Arranges **numbers and operations** inside the panel.

---

### **9. Add Components to Frame**
```java
frame.add(panel);
frame.add(negButton);
frame.add(delButton);
frame.add(clrButton);
frame.add(textField);
frame.setVisible(true);
```
- Adds all components to the main frame.

---

### **10. Implement Action Listener**
```java
@Override
public void actionPerformed(ActionEvent e) {
```
- Detects **which button** is clicked.

#### **Handle Number Buttons**
```java
for (int i = 0; i < 10; i++) {
    if (e.getSource() == numberButtons[i]) {
        textField.setText(textField.getText().concat(String.valueOf(i)));
    }
}
```
- Appends **clicked number** to the text field.

#### **Handle Decimal Button**
```java
if (e.getSource() == decButton) {
    textField.setText(textField.getText().concat("."));
}
```
- Appends a **decimal point**.

#### **Handle Arithmetic Operations**
```java
if (e.getSource() == addButton) {
    num1 = Double.parseDouble(textField.getText());
    operator = '+';
    textField.setText("");
}
```
- Stores `num1` and waits for the next number.

#### **Handle Equals Button**
```java
if (e.getSource() == equButton) {
    num2 = Double.parseDouble(textField.getText());
    switch (operator) {
        case '+': result = num1 + num2; break;
        case '-': result = num1 - num2; break;
        case '*': result = num1 * num2; break;
        case '/': result = num1 / num2; break;
    }
    textField.setText(String.valueOf(result));
    num1 = result;
}
```
- Performs calculation **based on the operator**.

#### **Handle Delete Button**
```java
if (e.getSource() == delButton) {
    String string = textField.getText();
    textField.setText(string.substring(0, string.length() - 1));
}
```
- Removes **last entered digit**.

#### **Handle Clear Button**
```java
if (e.getSource() == clrButton) {
    textField.setText("");
}
```
- Resets the calculator.

#### **Handle Negative Button**
```java
if (e.getSource() == negButton) {
    double temp = Double.parseDouble(textField.getText());
    temp *= -1;
    textField.setText(String.valueOf(temp));
}
```
- Converts the **current number to negative**.

---

