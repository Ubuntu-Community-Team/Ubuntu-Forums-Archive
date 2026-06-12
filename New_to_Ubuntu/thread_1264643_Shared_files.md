---
title: "Shared files?"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by paulmmj on 2009-09-12
Hello Ubuntu Forums,

I am attempting to share files with my Mac OS X Leopard computer. My computer shows up in the "Shared" area of OS X, but I am unable to "connect." I have performed all or at least most of all the "Help" within Ubuntu. Any advice would be greatly appreciated!

Thanks again,
Paul.

---

### Post by StuartN on 2009-09-12
I assume you have installed the packages necessary to enable sharing (you are asked when you first try to share a folder). And I assume the Mac can browse to the network and see the Linux box. What happens when you try to connect? Make sure that you are entering the Linux user's username and password.

---

### Post by paulmmj on 2009-09-12
My Linux machine appears on my Mac, but I am unable to connect or and the "Connect As" button appears unresponsive. I've also attempted connecting to my own IP, but then it simply takes me to my Ethernet box, and it doesn't accept my password anyway. I hate to sound dumb, but is there not some sort of program that I can do this with? I'm not really sure what is configured to do what...

---

### Post by paulmmj on 2009-09-12
Update* I can connect to my Ethernet box from my Mac, but I have nothing stored there and it did not make connecting to Linux work.

---

### Post by StuartN on 2009-09-12
I have Ubuntu 8.10 here with the Samba packages installed automatically when I first shared a folder, and I have restarted since installing Samba. I have a Mac with Leopard. In the Finder on the Mac I select Go -> Connect to Server and then enter smb://my_Linux_machine. It then prompts for my (Linux) username and password and displays all the shares I might want to connect.

(From another Linux machine I can see my_Linux_machine in the Network place, with a list of shares. It is invisible to the Mac until the first time connecting, and from then on it appears in the Finder.)

---

### Post by paulmmj on 2009-09-12
I don't know... I just really don't know. I cannot find anywhere to put in any information as regards to usernames, and sometimes my Ubuntu machine doesn't even show up. Could someone just walk me through a way to share files from Mac OS X Leopard to Ubuntu 9.04 Jaunty Jackolope?

---

### Post by paulmmj on 2009-09-12
Both my machines recognize each other somewhat... But I can't access physical files, or even look at the shared folder, but I can see it's there. On OS X, I can't connect. While on Ubuntu, I can "connect" so to speak, but I can't see anything, and if I add a file, it doesn't show up... Can anybody explain?

---

### Post by paulmmj on 2009-09-12
Hello Ubuntu Forums,

I recently put Ubuntu 9.04 Jaunty Jackalope on my Dell Dimension 4700. I also own a 13" Macbook Pro. I want to share files on my network between them. It was no problem when Windows was on, but now I just can't quite seem to work it out. Each computer knows the other is there, but is unable to connect to either. Ubuntu can even go so far to appear connected, but I can't access my shared files and anything I write there does not transfer to my Mac. Please, help? 

Thanks,
Paul.

---

### Post by falconindy on 2009-09-12
1. Install Samba on both machines
2. ?????
3. Profit!

---

### Post by overdrank on 2009-09-12
Threads merged.

---

