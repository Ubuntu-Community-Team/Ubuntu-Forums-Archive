---
title: "Mac OS X/Ubuntu network"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by johnlocke2342 on 2008-10-28
Hi.
I own a MacBook 4.1 running Mac OS X Leopard (and Ubuntu), and I'd like to learn how to share my documents between it and my Desktop PC running Ubuntu (8.10 RC).
I found some ways to do so on the french forums, but it seems it doesn't work anymore with 10.5.
If anyone could help.

Thanks in advance.

---

### Post by nixscripter on 2008-10-28
I would suggest setting up an NFS server on the Leopard box and just using Ubuntu's NFS client capabilities. A short introduction is here: [http://www.macresearch.org/nfs-exports-leopard](http://www.macresearch.org/nfs-exports-leopard)

Hope this helps.

---

### Post by dmizer on 2008-10-28
In my sig, there is a link for configuring Ubuntu NFS shares.

---

### Post by johnlocke2342 on 2008-10-29
Thanks for the answers!
Looks like my computers "see" each other, but I have a Permission Denied error on both sides.

---

### Post by nixscripter on 2008-10-29
It probably has to do with the user IDs being different between the two machines. If you're not worried about security, then you can configure each NFS server to squash all user IDs to your UID on each machine.

---

### Post by johnlocke2342 on 2008-10-29
It's strange, I see my Ubuntu Desktop in the Finder, but I can't access it, and I see my /Users/moise from my Mac in Ubuntu, but I can't access to the one or the other.

---

### Post by nixscripter on 2008-11-01
First, one thing occured to me I almost forgot about. You have to add "insecure" to your export options on your Ubuntu machine in order to let your Mac use an unpriviledged port to access it. Make sure that's the problem by opening a terminal on your Mac, and trying to mount it this way: ```
mkdir ~/newdir && sudo mount -P **your-server:/your/share** ~/newdir
```

Second, what is the message your Ubuntu machine gets when trying to mount your Mac when you do a similar thing in the terminal (without the -P flag, of course)?

---

### Post by hanzomon4 on 2008-11-01
> **nixscripter said:**
> First, one thing occured to me I almost forgot about. You have to add "insecure" to your export options on your Ubuntu machine in order to let your Mac use an unpriviledged port to access it. Make sure that's the problem by opening a terminal on your Mac, and trying to mount it this way: ```
mkdir ~/newdir && sudo mount -P **your-server:/your/share** ~/newdir
```

Second, what is the message your Ubuntu machine gets when trying to mount your Mac when you do a similar thing in the terminal (without the -P flag, of course)?

No if the Ubuntu desktop is the server and OSX is the client you need to add a special option to connect via the reserved ports "-o resvport"

---

