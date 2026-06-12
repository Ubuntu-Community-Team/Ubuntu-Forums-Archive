---
title: "Zend Studio 8 Installation"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by bubloo on 2011-03-20
Dear All

I am a newbie to Ubuntu and has recently sifted from windows.I develope profetional grade PHP applications. I am facing problems in installing Zend Studio 8 on ubuntu 10.10 64bit.I have Downloaded the ZendStudio8.0.tar.gz file and has also extracted it through the terminal command of tar zxvf Zenstudio8.0.tar.gz but when i run the binary file it says cannot execute binary files.I have seached and browsed tones of sites and even this forum but coudnt solve this problem. Your Help will be deeply apreciated.

Regards
bubloo

---

### Post by lykeion on 2011-03-20
It might be that you have to make the binary executable first.

GUI method:
Rightclick binary > Properties > Permissions tab > Check "Allow executing file as program"

Command-line method:
```
chmod +x <binary_file>
```

---

### Post by bubloo on 2011-03-20
> **lykeion said:**
> Check the installation guide pdf available here: [http://www.zend.com/en/products/studio/resources](http://www.zend.com/en/products/studio/resources)

yes i have checked that too, but i am getting the eror..!!!

---

### Post by bubloo on 2011-03-20
> **lykeion said:**
> It might be that you have to make the binary executable first.

GUI method:
Rightclick binary > Properties > Permissions tab > Check "Allow executing file as program"

Command-line method:
```
chmod +x <binary_file>
```

Thankyou for your reply

What i have done is 
cd to the directory where ZendStudio is located
then chmod +x ZendStudio
It donot responds anything

[HTML]bubloo@ubuntu:~$ cd '/home/bubloo/Downloads/Zenddd/ZendStudio' 
bubloo@ubuntu:~/Downloads/Zenddd/ZendStudio$ chmod +x ZendStudio
bubloo@ubuntu:~/Downloads/Zenddd/ZendStudio$ [/HTML]

---

### Post by lykeion on 2011-03-21
No response since the command did what you asked it for. :)

The next step would be (thought it was obvious) to launch the installer. You could do that in a terminal while in the same dir as the binary with:
```
./ZendStudio
```
From your output I suppose the binary installer name is ZendStudio. If that's not the case I suggest you to go to the Zend forums (It is a commercial product and if you paid for it you should be able to get help from them).

---

