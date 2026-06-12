---
title: "Install bin file problems"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by caramelsoul on 2010-02-21
I am having real trouble trying to install bin file. Apparently i need it to view ADVFN. It says i need to install it maually. 

I have downloaded it to my desktop. 

Location is /home/home/Desktop

File name is jre-6u18-linux-i586.bin

Iv done a search and dont really seem to be getting anywhere. Iv spent ages doing this and now its just annoying me. Can some one help please.

---

### Post by j.bell730 on 2010-02-21
```
cd ~/Desktop
chmod +x jre-6u18-linux-i586.bin
./jre-6u18-linux-i586.bin
```

Try those three commands.

---

### Post by caramelsoul on 2010-02-21
That seems to have worked and installed it. Thankyou.

But when i go to advfn.com and log in it is still asking me to manually install the java runtime environment and is directing me to the download page where i originally got the bin file. ADVFN seems to not want to run on my PC.

---

### Post by caramelsoul on 2010-02-21
I was reading something in previous posts about having to make a link to java and my browser. I am using swiftfox.

---

### Post by 3rdalbum on 2010-02-21
On Ubuntu, you use the Software Center or Synaptic Package Manager to install software wherever possible, rather than trawling the web for software. It's easier to install and easier to manage this way.

If you do a search for "jre" in Synaptic, you find "sun-java6-jre". If you right-click on it, under the Suggests submenu is "sun-java6-plugin" which gives you all the dependencies for running Java in your web browser.

If you install "sun-java6-jre" and "sun-java6-plugin" you should find ADVFN will work, after you quit your web browser.

---

### Post by caramelsoul on 2010-02-21
It seems to already have both of them installed already :(

---

### Post by F W Adams on 2010-05-12
Note for 10.04 users

Just some help and additional info. If you upgrade from a previous version to 10.04 you'll be fine but if it's a clean install of 10.04 then you'll find that sun-java6 isn't included in 10.04 but a replacement, OpenJDK.

If you have trouble go to the link below to get sun-java6. You need to open an additional depository to load sun-java6. Read the comments as well as the original instructions are not precisely right.

[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html/comment-page-1#comment-30009](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html/comment-page-1#comment-30009)

Mine now running ok with 10.04 & sun-java6.

---

