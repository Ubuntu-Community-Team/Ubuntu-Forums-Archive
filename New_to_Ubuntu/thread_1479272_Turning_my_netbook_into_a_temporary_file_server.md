---
title: "Turning my netbook into a temporary file server"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by 311005901 on 2010-05-10
I'm going to clean install Lucid on my computer and I have like 100gb+ of files. I usually put everything on my iPod for a temporary transfer, but it can only hold 80gb.

Is there a way I can transfer the files onto my netbook (runing Lucid) through FTP or some other way?

I just need a temporary solution for all of these files. I'm already using Dropbox for my music (50gb+) but my videos and documents are over 100gb.

Any suggestions?

---

### Post by spiky001 on 2010-05-10
I presume it is network to pc if so you can use ssh insatll ssh open server on laptop, also you might want to use filezilla as well 
They are both in synaptic manager

---

### Post by CharlesA on 2010-05-10
sftp would work. Just install ssh on the server and then use something like filezilla to ftp them over to the other machine.

Either that or you could use NFS, but there is more to configure then SSH/SFTP.

---

### Post by 311005901 on 2010-05-10
I'm not sure if I understand correctly.
Which computer do I install filezilla and ssh on?

Maybe I was a little vague...
I have a netbook and a regular desktop connected to the internet through a router. I need to transfer all of the files from the desktop to the netbook through the network. How do I do this?

---

### Post by spiky001 on 2010-05-10
install ssh openserver on laptop this will allow you to transfer files to it, install filezilla on desktop so you can transfer to server hope it helps

---

### Post by HarrisonNapper on 2010-05-10
As a note, if your netbook has a solid state drive, you may not want to do this. SSDs have fewer total writes in their working lifetime.

---

### Post by 311005901 on 2010-05-11
Thanks everyone for the replies! I'll try the transfer now! 

@HarrisonNapper: Thanks for the concern. I double checked to make sure I didn't have an SSD. Thankfully, I don't. I got the HP Mini with an HDD. Thanks for looking out for me! :)

---

