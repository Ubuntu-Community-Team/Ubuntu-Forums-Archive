---
title: "Ready to give up...."
date: 2008-12-13
forum: New to Ubuntu
---

### Post by bcondemi111 on 2008-12-13
Just want to install an hp driver I downloaded from the hp site.

its called 'hplip-2.8.10.run' and it was downloaded on the desktop

I read the site's instructions how to install. So I opened there terminal it says...

name@name-desktop:-'dollar sign'

I typed sh hplip-2.8.10.run and it returned

'Can't open hplip-2.8.10.run 

I'm so frustraded reading about the sudo command, root permissions....god damn! Can someone please, please tell me what to type in......

thanks.

---

### Post by ettercap on 2008-12-13
use "sudo .\hplip-2.8.10.run"

that should work !!

---

### Post by bcondemi111 on 2008-12-13
Yes I got it thank-you!!!

I also learned that I can rightclick the file 'allow executing a file'

I will write that command down and remember it next time as well

BC

---

### Post by theharshone on 2008-12-13
I felt the same way when I first started. Firstly on Linux, when you download a file, you cannot just execute it, for security purposes. If you want execute it, you have to type chmod +x </path/to/file>.

Second, the sudo command allows you to run an application with full access, read and write, to the entire hard drive. 

Thirdly, the application you are trying to install is available in the repositories. 

just type:

sudo apt-get install hplip.

---

### Post by bcondemi111 on 2008-12-13
I actually played with pclinuxOS a couple years back and had it on a dual boot along with Windoze. Root was a second password and allowed me to do anything. Left it after a while since a lot of hardware I had lacked the drivers I needed.
Decided to come back a try another Distro, hopefully this is the best!

Thanks for the responses!

BC

---

