---
title: "Disable usb drives.."
date: 2009-08-26
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-26
How to disable usb ports in ubuntu?

---

### Post by alexlafreniere on 2009-08-26
What exactly are you trying to accomplish by locking down USB ports? I assume for a public computer that you don't want people plugging USB drives into? One way you could do this is by creating a user account with very limited privileges that would include not being able to mount drives without an admin password.

---

### Post by karthick87 on 2009-08-27
yes u r right i dont want anyone one to plug usb drives..How to create a limited account?

---

### Post by NoaHall on 2009-08-27
System -> Admin -> Users and Groups -> Add User

Then, to stop the mounting

System -> Admin -> Authorisations -> Storage -> Mount file systems from removeable media -> Block -> User you just created

---

