---
title: "Need to know about repo"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by navaneethan on 2010-02-18
How to handle repository? I mean sometimes i pulled to install some of the packages from my dvd using synaptic...when i click the needed packages and apply to install ..after sometime error occurred ...it says like couldnot retrieve the package from ubuntu.archive.com.....like that

I don't know how to set repository ..if it is detail means happy to have

---

### Post by leonardo_neo on 2010-02-19
> **navaneethan said:**
> How to handle repository? I mean sometimes i pulled to install some of the packages from my dvd using synaptic...when i click the needed packages and apply to install ..after sometime error occurred ...it says like couldnot retrieve the package from ubuntu.archive.com.....like that

I don't know how to set repository ..if it is detail means happy to have

What packages exactly are you trying to install??

Is it for restricted packages?

I would recommend you to rather install the restricted packages from online package manager and not from your CD.

---

### Post by Sef on 2010-02-19
> How to handle repository? I mean sometimes i pulled to install some of  the packages from my dvd using synaptic...when i click the needed  packages and apply to install ..after sometime error occurred ...it says  like couldnot retrieve the package from ubuntu.archive.com.....like  that

I don't know how to set repository ..if it is detail means happy to have

Why are you installing from the DVD?

---

### Post by Mustard on 2010-02-19
I have a feeling that the main repositories are down atm..I know I can't connect.

---

### Post by stlsaint on 2010-02-19
> **navaneethan said:**
> How to handle repository? I mean sometimes i pulled to install some of the packages from my dvd using synaptic...when i click the needed packages and apply to install ..after sometime error occurred ...it says like couldnot retrieve the package from ubuntu.archive.com.....like that

I don't know how to set repository ..if it is detail means happy to have

The install is trying to download the packages from the online repository(which it is suppose to do) but your post gives the impression that you are trying to install packages from a ubuntu disc. Do you not have internet access?

---

### Post by stlsaint on 2010-02-19
> **Mustard said:**
> I have a feeling that the main repositories are down atm..I know I can't connect.

At time of this post main servers are up. I just checked.

---

### Post by navaneethan on 2010-02-20
I wanna to install from DVD....this is the easy way to get...only we need to know to configure repo....don't know the exact file name

---

### Post by navaneethan on 2010-02-20
> **Sef said:**
> Why are you installing from the DVD?

It is one of the method ...Many of the users are wanting like that.offline installation

---

### Post by oldos2er on 2010-02-20
With the DVD in the drive, run ```
sudo apt-cdrom add && sudo apt-get update
```

---

