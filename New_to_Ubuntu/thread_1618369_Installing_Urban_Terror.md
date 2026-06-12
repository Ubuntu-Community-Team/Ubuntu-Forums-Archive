---
title: "Installing Urban Terror"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by TheShaggz09 on 2010-11-10
I am completely new to Linux. I have only been using it for about a week. I don't know a lot about Terminal commands or anything. I do, however, like gaming, and am looking for FPS games to play. I heard Urban Terror is good, but I don't know how to install it. I downloaded it from the site, but it says it's marked as non-executable. If anyone could give me a step-by-step, it would be greatly appreciated. I look forward to learning more and more about Linux every day. Thanks in advance.

---

### Post by Decatf on 2010-11-10
Right click ioUrbanTerror.i386 (or.x86_64 if you're running 64-bit) and go to Properties. Under the Permissions tab, check "Allow executing file as a program". Double click the file to run it.

---

### Post by Jetso on 2010-11-10
What is the extension of the file you downladed?

---

### Post by dFlyer on 2010-11-10
You might want to check the following link:
[www.youtube.com/watch?v=Wma3vBpCtqs](www.youtube.com/watch?v=Wma3vBpCtqs)

---

### Post by I'mGeorge on 2010-11-10
well if you downloaded it from here [http://www.urbanterror.info/docs/texts/110/](http://www.urbanterror.info/docs/texts/110/), it's a zip file so first you have to extract it. Just install and use file-roller to extract it. Inside the extracted folder you would find executables for windows, linux i386 arechitecture and linux x86-64 architecture, something like ioUrbanTerror.x86_64 Just double click on the executable that fits your distro, and that's all.

---

### Post by ubudog on 2010-11-10
After you've extracted it with Archive Manger, run these commands in a terminal (Applications>Accessories>Terminal).  

```
cd UrbanTerror
```
```
chmod +x ioUrbanTerror.i386
```
```
./ioUrbanTerror.i386
```

And it'll start and ask you for your screen name.  It's also very helpful to watch the tutorial.

---

### Post by ubudog on 2010-11-10
> **dFlyer said:**
> You might want to check the following link:
[www.youtube.com/watch?v=Wma3vBpCtqs](www.youtube.com/watch?v=Wma3vBpCtqs)

That's a great video to watch too.

---

### Post by I'mGeorge on 2010-11-10
> **ubudog said:**
> 
```
cd UrbanTerror
```
```
chmod +x ioUrbanTerror.i386
```
```
./ioUrbanTerror.i386
```


Good point, so you would make sure they're executables. By the way see you in the game I think I'll go and play it a bit just about now.

---

### Post by Simian Man on 2010-11-10
Why is it not in the Ubuntu repositories?  It's in the Fedora ones.

---

### Post by NightwishFan on 2010-11-10
Urban Terror has non-free content I believe. It also seems to not like newer kernels or GCC. (It runs with terrible performance for me on Maverick and Debian Testing, but runs great on Lucid).

---

### Post by ubudog on 2010-11-10
> **NightwishFan said:**
> Urban Terror has non-free content I believe. It also seems to not like newer kernels or GCC. (It runs with terrible performance for me on Maverick and Debian Testing, but runs great on Lucid).

Also, it won't run correctly on older ATI hardware, you have to set down the color (bits?).

---

### Post by NightwishFan on 2010-11-10
I think it only runs right on Nvidia. My intel card can handle it, however the 64-bit version fails to load the interface and the 32-bit version is slow (same bug as what makes 64-bit fail).

Its playable though I have to use an alternate executable.

---

### Post by Zzl1xndd on 2010-11-10
I use the Games section over at Getdeb for UT and some other games not in the repo's 

[http://www.playdeb.net/updates/Ubuntu/10.10](http://www.playdeb.net/updates/Ubuntu/10.10)

[http://www.playdeb.net/updates/ubuntu/10.04/?q=urban](http://www.playdeb.net/updates/ubuntu/10.04/?q=urban)

---

### Post by ubudog on 2010-11-10
> **NightwishFan said:**
> I think it only runs right on Nvidia. My intel card can handle it, however the 64-bit version fails to load the interface and the 32-bit version is slow (same bug as what makes 64-bit fail).

Its playable though I have to use an alternate executable.

It runs no problem on my old ATI 3200 card.

---

### Post by NightwishFan on 2010-11-10
Something happen wrong with compiling something, which causes some odd performance loss (compiled with -O3?). There seems to be no direct workaround.

---

