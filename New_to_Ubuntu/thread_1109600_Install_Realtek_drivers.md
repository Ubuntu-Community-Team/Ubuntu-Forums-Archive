---
title: "Install Realtek drivers"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by sadicote on 2009-03-28
Why don't i ever get this right? 
sade@sade-desktop:~$ tar xjvf '/home/sade/Documents/LinuxPkg_5.11.tar.bz2' 
./realtek-linux-audiopack-5.11/
./realtek-linux-audiopack-5.11/Readme.txt
./realtek-linux-audiopack-5.11/version
./realtek-linux-audiopack-5.11/alsa-utils-1.0.19.tar.bz2
./realtek-linux-audiopack-5.11/install
./realtek-linux-audiopack-5.11/alsa-lib-1.0.19.tar.bz2
./realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11.tar.bz2
./realtek-linux-audiopack-5.11/test.wav.bz2
sade@sade-desktop:~$ cd '/home/sade/Documents/LinuxPkg_5.11.tar.bz2' 
bash: cd: /home/sade/Documents/LinuxPkg_5.11.tar.bz2: Not a directory
sade@sade-desktop:~$ cd LinuxPkg_5.11.tar.bz2
bash: cd: LinuxPkg_5.11.tar.bz2: No such file or directory
sade@sade-desktop:~$ chmod +x LinuxPkg_5.11
chmod: cannot access `LinuxPkg_5.11': No such file or directory
sade@sade-desktop:~$ :confused:

---

### Post by Denestria on 2009-03-28
```
cd /home/sade/Documents/realtek-linux-audiopack-5.11
```

---

### Post by sadicote on 2009-03-29
Thanks, could you have another go at it?

sade@sade-desktop:~$ cd /home/sade/Documents/realtek-linux-audiopack-5.11
bash: cd: /home/sade/Documents/realtek-linux-audiopack-5.11: No such file or directory
sade@sade-desktop:~$

I double clicked on the package and it turns out it had these packages inside it: alsa-driver-1.0.19-5.11.tar.bz2, alsa-lib-1.0.19.tar.bz2, and alsa-utils-1.0.19.tar.bz2 and also a test.wav.bz2.

I have successfully installed the alsa-driver-1.0.19-5.11.tar.bz2. Do you think i should install the lib and utils package also, similarly, or will they be installed automatically? and what about the test.wav.bz2?

you know what, i went ahead and did the same for the other two tarballs, got some warnings and 'noxml' error or something, but when previously, i had only 'Master' and "Capture' in my Alsa mixer, now i have a huge line of options like Head, PCM, Front, Front Mic, and most importantly, Surround!. I should probably let go now, but still, the test.wav.bz2..what is it and what do i do with it?

---

### Post by fballem on 2009-03-29
Could I please ask a favour (I'm a relative newbie, so please be kind and detailed)?

I have an ALC888 Realtek audio chip on my motherboard. I have never installed from source.

Could someone please provide detailed instructions for doing the installation. I have downloaded LinuxPkg_5.11.tar.bz2 and it is on my desktop.

I am running Jaunty (Beta).

Many thanks!

---

### Post by sadicote on 2009-03-29
From my experience as mentioned in the previous post, i can say that if you open your package by double clicking it, you will find a folder which has more than one package. It is these packages that you should unzipping and installing. Open the terminal, 
1) type 'tar xjvf /home/your username/Desktop/alsa-driver-1.0.19-5.11.tar.bz2' and press enter.

2) type 'cd alsa-driver-1.0.19/' and press enter

3) type './configure' and press enter

4) type 'make' and press enter

5) type 'sudo make install' and press enter, you will be prompted for your password, type it and press enter. When you type your password it wont be visible in the terminal, so take care to type it correctly or you will get an 'invalid password' message.

Repeat the same procedure for 'alsa-lib..' and 'alsa-utils..' packages.

HEY! i just noticed, you have 378 posts to your credit. You are yanking my chain, making fun of me, right? :lol:

---

### Post by fballem on 2009-03-29
> **sadicote said:**
> From my experience as mentioned in the previous post, i can say that if you open your package by double clicking it, you will find a folder which has more than one package. It is these packages that you should unzipping and installing. Open the terminal, 
1) type 'tar xjvf /home/your username/Desktop/alsa-driver-1.0.19-5.11.tar.bz2' and press enter.

2) type 'cd alsa-driver-1.0.19/' and press enter

3) type './configure' and press enter

4) type 'make' and press enter

5) type 'sudo make install' and press enter, you will be prompted for your password, type it and press enter. When you type your password it wont be visible in the terminal, so take care to type it correctly or you will get an 'invalid password' message.

Repeat the same procedure for 'alsa-lib..' and 'alsa-utils..' packages.

Thanks - I'll give this a try and let you know how I make out. Is there anything I need to watch out for - I'm running 64-bit Jaunty?

---

### Post by sadicote on 2009-03-29
64-bit and it's specific problems are way out of my league. Never used it.

---

