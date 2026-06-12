---
title: "Invoke Gedit from another application"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by nikhilneela on 2011-01-23
Hi all, This may sound weird but thats what i need. How do we invoke gedit(or for that matter any application) from some other application automatically. I am trying to develop a system which allows a user to work on an application that is present in the cloud and when the cloud disconnects(due to low bandwidth), the system must transfer the control to the local copy of that application. The ultimate goal is that the user must not be interrupted at all times. The system must take care of actively switching from cloud application to local application and vice versa. The first hurdle here is that i must be able to invoke an application(say Gedit) from another process. Any ideas???

---

### Post by santosh83 on 2011-01-23
> **nikhilneela said:**
> Hi all, This may sound weird but thats what i need. How do we invoke gedit(or for that matter any application) from some other application automatically. I am trying to develop a system which allows a user to work on an application that is present in the cloud and when the cloud disconnects(due to low bandwidth), the system must transfer the control to the local copy of that application. The ultimate goal is that the user must not be interrupted at all times. The system must take care of actively switching from cloud application to local application and vice versa. The first hurdle here is that i must be able to invoke an application(say Gedit) from another process. Any ideas???

The standard way under Unix to invoke another process is by fork() followed by exec(). The child process is overlaid with the new executable. But there are lots of related functions in the standard C library that offer different options. Also if your application uses threading then there are many other considerations. If your application is GUI based, then your GUI toolkit may itself offer friendlier wrappers over fork/exec. You also have to consider IPC, since your program will be closely interacting with & controlling the application (gedit.)

---

