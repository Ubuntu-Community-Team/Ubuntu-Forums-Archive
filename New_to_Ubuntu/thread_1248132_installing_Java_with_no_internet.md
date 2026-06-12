---
title: "installing Java with no internet"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by C0rrup73dP14gu3 on 2009-08-23
been at this for weeks and really haven't figured out how to install it. don't bother saying ```
sudo apt-get
```. i followed the instructions perfectly. whenever i do type su i get a authentication failure. chmod doesn't work. sudo -i then chmod doesn't work. i have to install everything through the terminal because i can't get internet, and before you ask it's Netzero



sorry if this is the wrong section.... i've been really frustrated lately because of this

---

### Post by sandyd on 2009-08-23
if you have no internet, how do you even intend to get the java installer onto your computer?

---

### Post by C0rrup73dP14gu3 on 2009-08-23
flash drive


i downloaded the self installing thing and it gave me a bin file

---

### Post by alexlafreniere on 2009-08-23
Try going to the library and downloading the .deb from Sun's website?

---

### Post by sandyd on 2009-08-23
> **C0rrup73dP14gu3 said:**
> flash drive


i downloaded the self installing thing and it gave me a bin file
move the bin file to your desktop
and then type this into the terminal.
hit the tab key to accept the licence agreement btw.

```

cd ~/Desktop
mv *.bin java.bin
sudo ~/Desktop/java.bin

```

---

### Post by C0rrup73dP14gu3 on 2009-08-24
> **carlee said:**
> move the bin file to your desktop
and then type this into the terminal.
hit the tab key to accept the licence agreement btw.

```

cd ~/Desktop
mv *.bin java.bin
sudo ~/Desktop/java.bin

```

k it installed directly to my desktop, cant delete or move it tho.

edit

 be better if i installed libxine1-ffmpeg or something along those lines seeing as im gonna be using it for video/audio

---

### Post by nikhilbhardwaj on 2009-08-24
no no no
dont do this
sudo ~/Desktop/java.bin
this extracts as root and to copy rename etc you'll need to use sudo again

instead do 
sh ~/Desktop/java.bin

and this won't add the variables JAVA_HOME and you'll need to make a link to the plugin for web browsers

follow this guide

[http://www.linuxfromscratch.org/blfs/view/stable/general/jdk.html](http://www.linuxfromscratch.org/blfs/view/stable/general/jdk.html)

---

### Post by C0rrup73dP14gu3 on 2009-08-24
is there any way to install the codecs manually seeing as that was my primary goal( installing the internet client and java to download the codecs ). i really don't want to compile everything seeing as it looks like a lengthy and complicated process. i did look and saw something about checkinstall. downloaded that and really didn't even do anything. doesn't even come up in whatever you wanna call it. 

without reading all that

better way to install libxine1-all-plugins without compiling and what not

---

### Post by colorpurple21859 on 2009-08-29
here is a link to get netzero up and running including installing java bin file
[http://www.linuxquestions.org/questions/slackware-14/netzero-628659/](http://www.linuxquestions.org/questions/slackware-14/netzero-628659/)

---

