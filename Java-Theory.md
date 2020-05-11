## Lập trình hướng đối tượng (Java)

  ***I. Khái niệm*** 
  
  - Là một kỹ thuật lập trình cho phép lập trình viên tạo ra các đối tượng trong 
  code trừu tượng hóa các đối tượng
  - Đối tượng là những sự vật, sự việc mà nó có những tính chất, đặc tính, hành động 
  giống nhau và ta gom góp lại thành đối tượng.

  ***II. Nguyên lí***  

   **1. Tính đóng gói** 
   - Các thuộc tính và phương thức có liên quan với nhau được đóng gói thành các 
    lớp để tiện cho việc quản lý và sử dụng
   - Đóng gói để che giấu một số thông tin và chi tiết cài đặt nội bộ để bên ngoài 
    không thể nhìn thấy.
   - Ví dụ:
     ```java
     public class Student {
       private String name;
	 
       public String getName() {
         return name;
       }
	 
       public void setName(String name) {
         this.name = name;
       }
     }
     ```

   **2. Tính kế thừa**
   - Kế thừa là sự liên quan giữa hai `class` với nhau, trong đó có `class`
   cha (superclass) và class con (subclass)
   - Khi kế thừa `class` con được hưởng tất cả các phương thức và thuộc tính của `class` 
   cha
   - Tuy nhiên, nó chỉ được truy cập các thành viên `public` và `protected` của `class` 
   cha. Nó không được phép truy cập đến thành viên `private` của `class` cha
   - Khi kế thừa từ một lớp đang tồn tại bạn có sử dụng lại các phương thức và thuộc 
   tính của lớp cha, đồng thời có thể khai báo thêm các phương thức và thuộc tính 
   khác.
   - Ví dụ:
     ```java
     class Employee {
       float salary = 1000;
     }
  
     class Programmer extends Employee {
       int bonus = 150;
     }
 
     public class InheritanceSample1 {
       public static void main(String args[]) {
         Programmer p = new Programmer();
         System.out.println("Programmer salary is: " + p.salary);
         System.out.println("Bonus of Programmer is: " + p.bonus);
       }
     }
     ```

  **3. Tính đa hình**
   
   - Đa hình là khái niệm mà hai hoặc nhiều lớp có những phương thức giống nhau 
   nhưng có thể thực thi theo những cách thức khác nhau.
   - Ví dụ:
     ```java
     class Shape {
       void draw() {
         System.out.println("drawing...");
       }
     }
 
     class Rectangle extends Shape {
       void draw() {
         System.out.println("drawing rectangle...");
       }
     }
 
     class Circle extends Shape {
       void draw() {
         System.out.println("drawing circle...");
       }
     }
 
     class Triangle extends Shape {
       void draw() {
         System.out.println("drawing triangle...");
       }
     }
 
     class TestPolymorphism2 {
       public static void main(String args[]) {
         Shape s;
         s = new Rectangle();
         s.draw();
         s = new Circle();
         s.draw();
         s = new Triangle();
         s.draw();
       }
     }
     ```

**4. Tính trừu tượng**
 - Tính trừu tượng nghĩa là chọn ra các thuộc tính, phương thức của đối tượng cần 
 cho việc giải quyết bài toán đang lập trình.
 - Ví dụ: Bài toán quản lý sinh viên chúng ta chỉ cần quản lý các thông tin như:  
	- Họ tên
	- Ngày sinh
	- Giới tính
	- Điểm thi  


   > mà lại không cần quản lý thêm các thông tin:   
	- Màu tóc  
	- Sở thích  
	- Chiều cao 
 
  ***III. Abstract và Interface***

  | Abstract | Interface | 
  | :-: |:-:| 
  | Thường giữa `abstract class` và `class` bắt nguồn từ nó có môi quan hệ khăng khít nhau | `Interface` và `class implement` không cần quá mật thiết | 
  | 1 `class` chỉ được bắt nguồn từ 1 `class` khác | 1 `class` có thể `implement` nhiều `interface` (đa kế thừa) |  
  | Có thể biểu thị các phần tử không `public` | Trong `interface` các `method` phải là `public` |   

  ***IV. Overloading và Overriding ( nạp chồng phương thức và ghi đè phương thức )***  
   
  | Overloading | Overriding | 
  | :-: |:-:| 
  | Nạp chồng phương thức được sử dụng để giúp code của chương trình dễ đọc hơn | Ghi đè phương thức được sử dụng để cung cấp cài đặt cụ thể cho phương thức được khai báo ở lớp cha | 
  | Nạp chồng được thực hiện bên trong một `class` | Ghi đè phương thức xảy ra trong 2 `class` có quan hệ kế thừa |  
  | Nạp chồng phương thức thì tham số phải khác nhau | Ghi đè phương thức thì tham số phải giống nhau |   
  |  Nạp chồng phương thức là ví dụ về đa hình lúc biên dịch | Ghi đè phương thức là ví dụ về đa hình lúc runtime |
  | Nạp chồng phương thức không thể được thực hiện khi chỉ thay đổi kiểu giá trị trả về của phương thức. Kiểu giá trị trả về và giá trị trả về có thể giống hoặc khác, nhưng tham số phải khác nhau | Giá trị trả về phải giống nhau |

   - Ví dụ về `overloading`:

     ```java   
     public class OverloadingExample {
       static int add(int a, int b) {
         return a + b;
       }
 
       static int add(int a, int b, int c) {
         return a + b + c;
       }
     }
     ```

   - Ví dụ về `overriding`:

     ```java
     class Animal {
       void eat() {
         System.out.println("eating...");
       }
     }
  
     class Dog extends Animal {
       void eat() {
         System.out.println("eating bread...");
       }
     }
     ```

  ***V. Array và ArrayList***
  
  | Array | ArrayList |
  | :-: | :-: |
  | Kích thước cố định | Kích thước có thể thay đổi được |
  | Có thể lưu trữ dữ liệu kiểu nguyên thủy và đối tượng | Chỉ có thể lưu trữ dữ liệu kiểu đối tượng |
  | Tốc độ lưu trữ và thao tác nhanh hơn | Tốc độ lưu trữ vào thao tác chậm hơn |
  | Chỉ có thuộc tính `length` | Có nhiều phương thức để thao tác với dữ liệu |

  - `ArrayList` sang `Array`
    
    ```java
    String[] item = arrayList.toArray(new String[arrayList.size()]);
    ```

  - `Array` sang `ArrayList`
  
    ```java    
    list2 = Arrays.asList(item);
    ``` 

  ***VI. Set, Map và List***
   
   - `Set`: là một collection không thể chứa 2 giá trị trùng lặp. `Set` được sử dụng để biểu diễn các bộ, chẳng hạn như bộ tú lu khơ, thời khóa biểu của học sinh, các   tiến trình đang chạy trên máy tính...
   - `List`: là một collection có thứ tự (đôi khi còn được gọi là một chuỗi). `List` có thể chứa các phần tử trùng lặp. Thường có quyền kiểm soát chính xác vị trí các   phần tử được chèn vào và có thể truy cập chúng bằng chỉ số (vị trí của chúng).
   - `Map`: là một đối tượng ánh xạ mỗi `key` tương úng với một giá trị. `Map` không thể chứa giá trị trùng lặp. Mỗi `key` có thể ánh xạ đến nhiều nhất một giá trị.

  ***VII. String, StringBuffer và StringBuilder***
   
  - `String` là không thể thay đổi (immutable)
  - `StringBuffer`, `StringBuilder` có thể thay đổi (mutable)
  - Về tốc độ xử lý `StringBuilder` là tốt nhất, sau đó `StringBuffer` và cuối cùng mới là `String`.

  | StringBuffer | StringBuilder |  
  | :-: | :-:|  
  | `StringBuffer` là đồng bộ (synchronized) tức là luồng an toàn. Điều này có nghĩa là không thể có 2 luồng cùng truy cập phương thức của lớp `StringBuffer` đồng thời | `StringBuilder` là không đồng bộ (non-synchronized) tức là luồng không an toàn. Điều này có nghĩa là có 2 luồng cùng truy cập phương thức của lớp `StringBuilder` đồng thời |  
  | `StringBuffer` không hiệu quả bằng `StringBuilder` | `StringBuilder` hiệu quả hơn `StringBuffer` |

  ***VIII. this và super***

  **1. this**

  - Từ khóa `this` trong java là một biến tham chiếu được sử dụng để tham chiếu tới 
  đối tượng của lớp hiện tại.
  - Ví dụ:
    ```java
    class Student11 {  
      int id;  
      String name;  
      
      Student11(int id,String name){  
        this.id = id;  
        this.name = name;  
      }  
    }
    ```

   **2. super**
   - Từ khóa `super` trong Java là một biến tham chiếu mà được sử dụng để tham chiếu 
     đến đối tượng lớp cha gần nhất. Bất cứ khi nào bạn tạo instance (sự thể hiện) 
     của lớp con, một instance của lớp cha được tạo ngầm định, được tham chiếu bởi 
     biến super.
   - Ví dụ:
     ```java
     class Vehicle{  
       int speed=50;  
     }  
  
     class Bike4 extends Vehicle{  
       int speed=100;  
      
       void display(){  
         System.out.println(super.speed); //bay gio se in speed cua Vehicle  
       }  
       public static void main(String args[]){  
         Bike4 b=new Bike4();  
         b.display();  
     
       }  
     }  
     ```

  ***IX. static và final***
  
   **1. static**

   - Từ khóa `static` được sử dụng để quản lý bộ nhớ tốt hơn và nó có thể được truy  cập trực tiếp thông qua lớp mà không cần khởi tạo
   - Từ khóa `static` thuộc về lớp chứ không thuộc về instance (thể hiện) của lớp
   - Biến `static` có thể được sử dụng làm thuộc tính chung, để dùng chung dữ liệu  cho tất cả objects (hoặc instances ) của lớp đó và điều đó giúp cho chương trình tiết kiệm bộ nhớ hơn
   - Biến `static` sẽ lấy bộ nhớ chỉ một lần, nếu bất cứ đối tượng nào thay đổi giá   trị của biến `static`, nó sẽ vẫn ghi nhớ giá trị của nó.
   
   **2. final**

   - Biến `final`: khi một biến được khai báo với từ khoá `final`, nó chỉ chứa một giá trị duy nhất trong toàn bộ chương trình (hay dễ hiểu hơn gọi là biến hằng).
   - Phương thức `final`: khi một phương thức được khai báo với từ khoá final, các  `class` con kế thừa sẽ không thể ghi đè (override) phương thức này
   - Lớp `final`: khi từ khoá `final` sử dụng cho một lớp, lớp này sẽ không thể được  kế thừa
   - Biến `static final` trống: Một biến `final` mà không được khởi tạo tại thời điểm khai báo được gọi là biến `final` trống.