---
title: "Wireless Card: Need Desperate Help"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Cure777 on 2006-08-03
I just installed Xubuntu on my laptop, an old Dell Inspiron 3800. With it I have a new Wireless-G Linksys wireless card, model WPC54G. Right now I am posting on my desktop. Is there anyway to get his card working with my laptop? Please help. Thanks.](*,)

---

### Post by Jagot on 2006-08-03
Have a look here:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

The card seems to be mentioned a few times.

---

### Post by Cure777 on 2006-08-03
Thank you. It seems my card is supported, but how do I know what version I have?

:EDIT:

I see. I will go about installing it...

---

### Post by Jagot on 2006-08-03
Issue the command lspci in Terminal and it should tell you which version you have - should be labelled as network controller or somethign along those lines.

---

### Post by Cure777 on 2006-08-03
> Couldn't get any of the windows drivers from linksys.com to work (they don't have a version 3 one listed right now) but I tried the driver off the installation cd with ndiswrapper and it worked like a charm! Just follow normal ndiswraper driver installation with the NT driver from the linksys install cd that comes with the card (built in driver works flawlessly with the 2.6.15 kernel, ndiswrapper not needed. Do not know if it will work for install.)

I located the drivers, and I put the tar.gz file of ndiswrapper on my computer, but the install file is very vague and I am extremely confused...could someone please help?

BTW, how do I know what kernal i have? is it 6.06?

---

### Post by Cure777 on 2006-08-03
also, "make" commands and such don't work...keep in mind I'm using xubuntu, 6.06........](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Jagot on 2006-08-04
Ndiswrapper is available in the repositories.  From Terminal:

```
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

To find out what kernel you're using in Terminal:

```
uname -a
```

You do not need to compile ndiswrapper (the stuff to do with the make command).  Install it as I previously mentioned.  However, for future reference, you probably need to install a package which links to various compliers.  Again.  from Terminal:

```
sudo aptitude update
sudo aptitude install build-essential
```

---

