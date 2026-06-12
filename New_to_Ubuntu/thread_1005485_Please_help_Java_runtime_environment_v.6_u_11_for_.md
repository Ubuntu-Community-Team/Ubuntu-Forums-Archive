---
title: "Please help Java runtime environment v.6 u 11 for 64 bit AMD?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by onlyonesock on 2008-12-08
Although I have various forms of JRE in my computer, I don't have upgrades 10/11. I can't get them from repositories because there is no 64 bit version yet. I downloaded upgrade 11 on my desktop and got it into a file for unpacking,thanks to help on here, but on trying to unpack it, I hit an error. That's as far as I got. Is anybody prepared to help me at this point? I am way out of my depth, I don't know much about computers at all, nor am I that keen to learn. I should call someone in but I can't find anybody locally - and as I'd really like to be able to use my favourite chat again and not throw the computer out of the window, I'm prepared to engage in a polite exchange with a patient knowledgeable, altruist, if there is one prepared to take me on.
Thanks

---

### Post by gn2 on 2008-12-08
Starting at the start, why do you want to upgrade to 11 from 10 ?

---

### Post by onlyonesock on 2008-12-08
Thanks gn2 :)

I don't. My version is u5. I need to get up to 10/11 to use my favourite chat programme

---

### Post by gn2 on 2008-12-08
Have you tried using Ubuntu 8.10 64-bit which has 10: sun-java6-jre (6-10-0ubuntu2)

---

### Post by onlyonesock on 2008-12-09
No. I have Ubuntu 8.04. So, you think it will help? If so, I'll do it

---

### Post by Therion on 2008-12-09
I'm pretty sure that by installing the **ubuntu-restricted-extras** package your Java and Flash issues will be taken care of.  Just enable the Medibuntu repository and then search for and install the package via Synaptic.

I mean, sure, you could upgrade to 8.10 if you want of course.  This just seems like it might a little simpler solution to the issue at hand.

Step One - Add the repo:```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Step Two - Add the GPG Key: ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Step Three: Install the ubuntu-restricted-extras package.

*Voila*.

---

### Post by gn2 on 2008-12-09
> **Therion said:**
> I'm pretty sure that by installing the **ubuntu-restricted-extras** package your Java and Flash issues will be taken care of.  

I think the current version in the 8.04 repository is 7 and the OP needs at least 10?

---

### Post by Therion on 2008-12-09
Well there is no 64-bit SUN Java of course - you have to use Iced Tea or OpenJDK.  And as I recall, the Medi-repo installs one, the other or both.  Installing restricted-extras might work and it might not; but it beats doing a fresh install if it does and there's no harm done if it doesn't.

---

### Post by gn2 on 2008-12-09
> **Therion said:**
> Well there is no 64-bit SUN Java of course - you have to use Iced Tea or OpenJDK.

That's odd?
Here's a list of some of the packages installed on my 64-bit Ubuntu 8.04: ```
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/jli
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/jli/libjli.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/xawt
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/xawt/libmawt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libj2pkcs11.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libnet.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libnio.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libnpt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjaas_unix.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libj2pcsc.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libverify.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/librmi.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libioser12.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libfontmanager.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjsoundalsa.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libzip.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/native_threads
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/native_threads/libhpi.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libhprof.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libj2gss.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libattach.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjsound.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libmlib_image.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/motif21
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/motif21/libmawt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libJdbcOdbc.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjava_crw_demo.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libunpack.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjava.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjawt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libnative_chmod.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjdwp.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libnative_chmod_g.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/server
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/server/libjvm.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/server/Xusage.txt
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libsplashscreen.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libdcpr.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libdt_socket.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjpeg.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libjsig.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libinstrument.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/headless
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/headless/libmawt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libsaproc.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libawt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libcmm.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/libmanagement.so
```

---

### Post by onlyonesock on 2008-12-09
Thank you. I have both OpenJDK and Iced tea but they don't do it for me. I have also just tried to upgrade to Ubuntu 10 as per ubuntu instructions with the system manager and although a series of windows demonstrated an upgrade was happening, after restart my system monitor still shows 8.04

---

### Post by Therion on 2008-12-09
> **gn2 said:**
> That's odd?
Here's a list of some of the packages installed on my 64-bit Ubuntu 8.04: 
I should have been more specific:  There is no 64-bit Sun Java ***browser plug-in***.

---

