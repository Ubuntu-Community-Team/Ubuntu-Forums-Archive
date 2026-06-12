---
title: "Restricted extras"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by mbele3000 on 2009-02-27
Hey Folks! 

 I know that usually when you download Ubuntu that to activate the "RESTRICTED EXTRAS" that you need to have to do so usually in terminal or in synaptic. Is there a way to download them to my desktop so that when I make the ISO that they are already included (for a computer without a internet connection)? Or is there a Ubuntu ISO download that already includes them as to save time? I have downloaded them (rest. extras) manually and then when I went to install them the public key was missing and well it would not install.... Is this possible and if so how?!
  
  Thanks ! Mbele 3000 --

---

### Post by powder on 2009-02-27
You might want to check out APTonCD.  I haven't tried it myself yet so I won't be much help but it sounds like what you are looking for.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Therion on 2009-02-27
Download **Super Ubuntu**

[http://hacktolive.org/wiki/Super_Ubuntu](http://hacktolive.org/wiki/Super_Ubuntu)

DL link at the bottom of the page.

---

### Post by mbele3000 on 2009-02-27
OK well is there a way to download the Ubuntu Studio Package's then so that if I install Super Ubuntu that I can just install the audio, video, and graphical package over it?

---

### Post by mbele3000 on 2009-02-27
BTW thanks for the lightning fast reply ! My heads still spinning! AND IS the reason that Ubuntu kicks BUTT! If I were looking for a answer in winblows Id be searching for days! Again thank you ALL!

---

### Post by Xiong Chiamiov on 2009-02-27
You should be able to include Ubuntu Studio's repository in Super Ubuntu's sources.list, although I'm not sure if that would introduce fun conflicts.

BTW, there's an edit button in the bottom left of your posts.

---

### Post by mbele3000 on 2009-02-27
OK is there a way that through synaptic that I can down load the Ubuntu Studio packages into a folder? Because the machine that Im using for the down load is really old and I know that much of it would not be supported or would only do a partial install. Then I could possibly use the apt on cd to create a package cd?

   "COOPERATION IS THE FUNDAMENTAL BASIS OF SUCCESS!!!"

---

### Post by achase79 on 2009-02-27
I have a computer without internet and I use synaptic's "package download scripts" to download the packages then I use terminal to cd into that directory then 
```
sudo dpkg -i *.deb
```
This will install the packages.

---

### Post by mbele3000 on 2009-02-27
Well this may sound like a idiot question but where do I download the scripts form? I'm gonna be a baby till my grave. Thank You BTW! But my brain hungers for more knowledge ! 

 OK I READ what you wrote I AM MORON ! LOL THANK YOU !

---

