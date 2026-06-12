---
title: "Don't know how to Install Wine without an Internet Connection"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by gregoryshock on 2011-05-27
I managed to install my first Ubuntu System Sunday.  I works great!   But I have just one catch that is keeping me from moving on in my learning.  I have a Verizon Wireless Modem LG VL600.  On Windows one must use the VZaccess Manager, to log on.  (There is no password, you just install and click connect)  I was told that if I install wine, then I could install the VZaccess Manager.  My Big problem is, without the modem I can't get online.  Otherwise, installing wine would be easy.  I went to the Howtogeek forums, and asked about it.  They helped me fine wine on the internet.  I managed to down load a file called wine-1.3.20.tar.bz2.  But I have no idea what to do with it.  Under Ubuntu, It is nothing more than a zip file.  Ok so I extract it, Then what?  I was told that I needed to use the terminal, and use the command lines.  But I'm too new to Linux, to understand the command lines.  Granted in High School, I messed with it a little.  I know that LS lists stuff.  And I know CP does something.  But that is all I know.  Can anyone tell me how or where I can learn the lines, and how to get this wine installed?  I realize that some people have found ways to run a verizon wireless modem without the VZ Manager.  But my plan is a limited one.  Meaning I'm only allowed to download 10 gigs a month. The VZ Manager keeps track of how much I've used.  So I think it's a good idea, if I can, to at least try to get the VZ manager installed.

---

### Post by ApOgEEs on 2011-05-27
In order to install wine without internet connection, you have to download all required packages. Here is the steps:

[LIST=1]
[*]Find any computer which have internet connection and go to this site:
[http://apt-web.dahsy.at/](http://apt-web.dahsy.at/)

[*]Select your base distribution.

[*]Select the mirror to download

[*]Type 'wine' in the Packages field

[*]Click submit

[*]you will get a list of *.deb files to download. Download all of them.

[*]Open your ubuntu pc and install all *.deb files you just downloaded by double clicking on the file. You may follow the list order (on the apt-web page) from top to bottom.
[/LIST]

Another way to install is by connecting your Ubuntu PC with wired internet connection and follow this instructions:
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by gregoryshock on 2011-06-04
[LIST=1]
[*]Find any computer which have internet connection and go to this site:
[http://apt-web.dahsy.at/](http://apt-web.dahsy.at/)
[*]Select your base distribution.  (How do you know what is your Base Distribution?)
[*]Select the mirror to download  (How do you know what mirror to download from?)
[*]Type 'wine' in the Packages field
[*]Click submit
[*]you will get a list of *.deb files to download. Download all of them.
[*]Open your ubuntu pc and install all *.deb files you just downloaded  by double clicking on the file. You may follow the list order (on the  apt-web page) from top to bottom.
[/LIST]

---

### Post by ApOgEEs on 2011-06-05
> **gregoryshock said:**
> [LIST=1]
[*]Find any computer which have internet connection and go to this site:
[http://apt-web.dahsy.at/](http://apt-web.dahsy.at/)
[*]Select your base distribution.  (How do you know what is your Base Distribution?)
[*]Select the mirror to download  (How do you know what mirror to download from?)
[*]Type 'wine' in the Packages field
[*]Click submit
[*]you will get a list of *.deb files to download. Download all of them.
[*]Open your ubuntu pc and install all *.deb files you just downloaded  by double clicking on the file. You may follow the list order (on the  apt-web page) from top to bottom.
[/LIST]

Your base distribution is the type of ubuntu you are using. For example, if you are using Ubuntu 11.04, then select Ubuntu 11.04 from the list.

You can choose mirror server which is near to your location. You may also leave it as default if you have no idea which one is nearest to your location.

---

### Post by gregoryshock on 2011-06-06
Ok, I think I did everything right, but for some reason the files wouldn't install.

---

### Post by donut123 on 2011-06-06
I dont think you can install anything without  a connection to the net. i dont see how it could be possible.

---

### Post by sectshun8 on 2011-06-06
> **gregoryshock said:**
> Ok, I think I did everything right, but for some reason the files wouldn't install.

Of course they wouldnt, and because I'm in the same boat I can tell you why.  Even though you've told everyone you have no internet connection on your Ubuntu machine, they somehow still assume you had it at one time to install all of the packages that Ubuntu does not come with... because if you don't install all of those first, nothing else is going to install.

I installed 11.04 on my netbook via a disc and USB dvd drive.  I work offshore and cannot connect it via the internet until I get back on land... which thankfully is in two days.  Anyhow, I've tried installing things like Conky, or even ZSNES by downloading them from a work PC and using USB, but because those installations are dependent on other things being installed first, I'm kinda SOL.  And even then, those dependencies are dependent on others and its a never ending cycle.

Without having 'net from the moment of install to download all the required updates, 11.04 is pretty much DOA... I hate it's not a full image installation like Mint or some other distros, but oh well.

---

### Post by Mark Phelps on 2011-06-06
I have the same device and I think you are NOT going to be able to get it to work other than under MS Windows ...

My experience using that modem is that it is flaky at best -- and that is even with installing the weekly updates to VZAM.  

Also, you will need to install the modem drivers -- which you can NOT do using Wine. You will need to connect to a wired Internet connection to even get the drivers. And, since you don't have one WITHOUT the modem working -- you're stuck on a catch-22.

---

### Post by gregoryshock on 2013-02-09
> **Mark Phelps said:**
> I have the same device and I think you are NOT going to be able to get it to work other than under MS Windows ...

My experience using that modem is that it is flaky at best -- and that is even with installing the weekly updates to VZAM.  

Also, you will need to install the modem drivers -- which you can NOT do using Wine. You will need to connect to a wired Internet connection to even get the drivers. And, since you don't have one WITHOUT the modem working -- you're stuck on a catch-22.

I gave up.

---

### Post by wildmanne39 on 2013-02-10
Old thread closed.

---

