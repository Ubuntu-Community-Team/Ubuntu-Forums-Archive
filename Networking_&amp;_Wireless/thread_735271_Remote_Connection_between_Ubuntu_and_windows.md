---
title: "Remote Connection between Ubuntu and windows"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by speedwiz7779 on 2008-03-25
Hello all

I've got Ubuntu working flawlessly, and now have a question.

I've got a personal computer at home, and one at work, and I would like to know how I would be able to access my work one (running Windows) from my home one (running Ubuntu 7.10)

Is it an easy process or will it get complicated??

Thanks all

---

### Post by rickyjones on 2008-03-25
> **speedwiz7779 said:**
> Hello all

I've got Ubuntu working flawlessly, and now have a question.

I've got a personal computer at home, and one at work, and I would like to know how I would be able to access my work one (running Windows) from my home one (running Ubuntu 7.10)

Is it an easy process or will it get complicated??

Thanks all

1) Enable remote desktop on your work PC.
2) Make sure that the remote desktop port (3389) is open on the router at your work and is pointed at your work computer.
3) Use the terminal services client on your Ubuntu computer to connect to your work computer using RDP. You'll need to provide the public IP address for your work internet connection.

This should work. Of course, this is a very simplified version because you did not include all necessary information.

-Richard

---

