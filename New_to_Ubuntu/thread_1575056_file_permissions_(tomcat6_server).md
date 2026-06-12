---
title: "file permissions (tomcat6 server)"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by govinsb on 2010-09-15
[FONT=Comic Sans MS][SIZE=3]I insatlled a tomcat6 server. I am trying to send  a message ( in encoded form ) from a client.java program using java URL class to a java servlet program in /var/lib/tomcat6/webapps/ROOT/WEB-INF/classes/ directory[/SIZE][/FONT][SIZE=3]. I redirect the message sent into a file output.txt. The file is created but when I open to see the file, it is empty and says readonly file and that I can't edit it. How to solve this problem? Is this a problem of permissions somewhere ?
[/SIZE]

---

### Post by cavh on 2010-09-15
If the file created by your app is empty, it would seem that your app isn't functioning as intended. What happens if you choose to output it to somewhere outside of Tomcat, can you try that? Ideally you should be writing a unit test and getting that to pass before worrying about the Tomcat part ...

---

### Post by govinsb on 2010-09-16
the problem was that i had used :- 
1. public void doGet  (HttpServletRequest req, HttpServletResponse res)
2. public void doPost (HttpServletRequest req, HttpServletResponse res)

and I had commented doGet part of the servlet code, which later, was resolved on uncommenting.

Now the problem is that :-
 When i open a file in doGet section, it easily gets created, but when i open the file from the doPost section, it doesn't happen so.
I am sending the input from client as usual.

---

### Post by cavh on 2010-09-17
You're betting off posting your actual code and questions on somewhere like [http://www.coderanch.com]("http://www.coderanch.com") than here, I think. Coderanch is a very active site devoted (mainly) to Java.

---

