---
title: "how to run android on ubuntu 11.04"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by jegatheeshmoorthy on 2011-08-29
Hi All,
     I am new to linux. I am using ubuntu 11.04 version (32-bit) , intel core 2 duo process.
I want to run android in this OS. I found lots of tutorial. In that they said need first install java then they say install ia32-libs. I have installed java successfully . but Iam not found the ia32-libs repo.
can any one guide how to install that one.

Thanks for Advance,
j moorthy.:confused::confused:

---

### Post by ubudog on 2011-08-30
Check this out:
[http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml](http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml)

---

### Post by jegatheeshmoorthy on 2011-08-31
Hi ,
    Thanks for your reply, I already I saw this one. In that -->*Synaptic Package Manager showing the ia2-libs package is not shown in my Ubuntu packages.*
 
*Thanks,*

---

### Post by kurok on 2011-08-31
you said your running the 32 bit version so im thinking thay are already installed on your system.It says in the instructions that you need to dl the 32 bit ones if your running a 64 bit system.

---

### Post by elliotn on 2011-08-31
Android SDK has an emulator I think

---

### Post by ubudog on 2011-08-31
> **elliotn said:**
> Android SDK has an emulator I think

Indeed.  In tools/emulator I believe.

---

### Post by jegatheeshmoorthy on 2011-08-31
> **kurok said:**
> you said your running the 32 bit version so im thinking thay are already installed on your system.It says in the instructions that you need to dl the 32 bit ones if your running a 64 bit system.
Hi Kurok,
    Hw I can identify that ia32-libs are present?
 
Thanks,

---

### Post by jegatheeshmoorthy on 2011-08-31
> **ubudog said:**
> Indeed.  In tools/emulator I believe.
Hi Ubudog,
    I download Android-linux . In that Ubuntu consider emulator, android, ddms that as a file with no extension( i.e , .exe, .jar ). So how I can open it?
 
thanks

---

### Post by 3rdalbum on 2011-08-31
> **jegatheeshmoorthy said:**
> Hi Ubudog,
    I download Android-linux . In that Ubuntu consider emulator, android, ddms that as a file with no extension( i.e , .exe, .jar ). So how I can open it?
 
thanks

What do the instructions say about how to run the emulator?

On a 32-bit system, there's no ia32-libs package, because all your libraries are 32-bit already. You don't need the package, it's redundant, it contains what you already have on any 32-bit Linux system.

---

### Post by ubudog on 2011-08-31
> **jegatheeshmoorthy said:**
> Hi Ubudog,
    I download Android-linux . In that Ubuntu consider emulator, android, ddms that as a file with no extension( i.e , .exe, .jar ). So how I can open it?
 
thanks

Hi, go into a terminal and type the following:
```
cd extractedsdkfolder/tools/
```

Then:
```
./android
```

Add an Android virtual device.  (look in "Available Packages", check "Android repository")  Download the "SDK Platform Android 3.2".  After that, go back to the main page and select "New".  Fill in the fields, using Android 3.2 as the target.

Now, click on your added virtual device, and click start.  The emulator should start with Android 3.2!

Note: The emulator takes a while to start, but should run fairly fast.

---

