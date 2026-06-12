---
title: "Ugrading from ver 8 to 9.0.4 from cd"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by kazv on 2009-06-06
Hi all.

im really really new at this, so be gentle.

i downloaded 9.0.4 twice. BUT for what ever reason it won auto run when i boot. up. 

is there a way i can upgrade once ubuntu is open. 

my bandwith is really slow and my SP refresheshes the dns every 2 hours so when i try and upgrade from the update date manager i drop the connection.

plese can somebody give me a "DUMMY" guide to do this.

bear in mind this this is all new to me

thanks

kaz

---

### Post by Elfy on 2009-06-06
I would imagine that either the download you burnt was either corrupt, the burn was bad or you don't have the pc/laptop set to bootfrom cd first.

Check that the md5sum is correct - you can check this from the terminal. Assuming that it was downloaded to the desktop do this - if the iso is elsewhere then change to that folder instead.

```
cd Desktop
md5sum ubuntu<tab>
```

using tab will autocomplete the file name - I don't know which version you downloaded.

The various md5sum's can be found here - [http://releases.ubuntu.com/9.04/MD5SUMS](http://releases.ubuntu.com/9.04/MD5SUMS)
Check the number reported in terminal with the coorect number form the list.

Did you burn the download as an image - it needs to be so in order to boot from it - if you burnt it as data then it will not work.

You can upgrade from the existing install but if the connection fails it will be less than good ... not sure what you could about that tbh. 

To upgrade however by cd you need to have the alternate and not the livecd.

If you do have issues with getting a good download you can order a cdfrom shipit.

---

### Post by zvacet on 2009-06-06
As **forestpixie** said you can not upgrade with live CD.you can do fresh install,but if you want to do that make separate home if you don´t already have one.you can follow [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.When you are done with that you can proceed.

Download same iso with torrent and point download to the folder with your existing iso.Torrent will just check corrupted files and replace them eith good ones.So,that way you will not download full iso,just some files.After that follow [this]("https://help.ubuntu.com/community/BurningIsoHowto") instructions.

---

