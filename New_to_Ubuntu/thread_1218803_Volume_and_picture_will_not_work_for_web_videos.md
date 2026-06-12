---
title: "Volume and picture will not work for web videos"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by GumpTron on 2009-07-21
To Whom It May Concern,

I purchased Ubuntu from my local computer guy and I am having trouble with it. He told me to come here for any help because he is very busy at the moment. So here is my issue.

I have installed Ubuntu and things seem to be working fine as far as the OS go. However, when i watch a Youtube video I am not able to adjust the colume of the video using the controls within youtube, i can only alter the volume by using the master OS volume. Can this be fixed?

I am also having trouble watching videos on other websites, [www.tube8.com](www.tube8.com) for example. I visit tube8.com and I can not even get a video to play. The buttons all flicker and stuff but they don't start the video when pressed.

I have confirmed that i am able to use these functions running Vista, so i know its not the websites fault.

Can anyone help? It is greatly appreciated.

Thank you :D

---

### Post by Crunchy the Headcrab on 2009-07-21
What version of Ubuntu do you have?  Jaunty 9.04?  Do you have the 32-bit or 64-bit version?

I hope you didn't pay too much more than the cost of a cd/dvd because ubuntu is free from many sources.  The only reason I can think to pay for it is to receive support, which it doesn't appear that your "computer guy" is giving you.

---

### Post by GumpTron on 2009-07-21
pretty sure its the 64 bit edition, my laptop is 64 bit. Ummm, i have the most recent version i think. It says its jaunty jackelope release 2009


I paid $60 for it. What do you mean it's free?

---

### Post by Temposs on 2009-07-21
Ubuntu is a completely free operating system. There is no need to pay anything for it. 

Unless you're getting something special like software/system support for it(as in, the guy who sold it to you promises to help you with your Ubuntu problems), you shouldn't be paying $60 for Ubuntu. At most you should pay the cost of the CD, which is less than $1.

---

### Post by GumpTron on 2009-07-21
> **Temposs said:**
> Ubuntu is a completely free operating system. There is no need to pay anything for it. 

Unless you're getting something special like software/system support for it, you shouldn't be paying $60 for Ubuntu. At most you should pay the cost of the CD, which is less than $1.

:confused:


ummmm, soooo.... he ****** me?

---

### Post by Temposs on 2009-07-21
It seems like the problem you're having is with the flash player. You likely have the 64-bit flash player installed. You may want to replace it with the 32-bit flash player, which is more stable, and works fine in Ubuntu.

I don't have any 64-bit machines, so I don't know the actual issues with the 64-bit flash player. Someone else will help with that.

---

### Post by .nedberg on 2009-07-21
> **GumpTron said:**
> 


ummmm, soooo.... he ****** me?

Yes, he did!

---

### Post by Temposs on 2009-07-21
> **GumpTron said:**
> :confused:


ummmm, soooo.... he ****** me?



Go to [www.ubuntu.com](www.ubuntu.com) and read "The Ubuntu Promise" at the bottom of the page:

The Ubuntu promise

    * Ubuntu will always be free of charge, including enterprise releases and security updates.
    * Ubuntu comes with full commercial support from Canonical and hundreds of companies around the world.
    * Ubuntu includes the very best translations and accessibility infrastructure that the free software community has to offer.
    * Ubuntu CDs contain only free software applications; we encourage you to use free and open source software, improve it and pass it on.

---

### Post by GumpTron on 2009-07-21
> **Temposs said:**
> It seems like the problem you're having is with the flash player. You likely have the 64-bit flash player installed. You may want to replace it with the 32-bit flash player, which is more stable, and works fine in Ubuntu.

I don't have any 64-bit machines, so I don't know the actual issues with the 64-bit flash player. Someone else will help with that.

thanks Temposs i will try that. Where do i get the other version?

---

### Post by Temposs on 2009-07-21
Another thing might be that you didn't install Adobe's flash player. They give you a choice of three different flash players when you first go to a flash site on Ubuntu, and only Adobe's flash player will play everything well.

---

### Post by GumpTron on 2009-07-21
> **Temposs said:**
> Another thing might be that you didn't install Adobe's flash player. They give you a choice of three different flash players when you first go to a flash site on Ubuntu, and only Adobe's flash player will play everything well.


ill try that as well, but where do i find it?

---

### Post by Temposs on 2009-07-21
What I'd like you to do is open Synaptic Package Manager through the System->Administration menu. Then, press Ctrl-F and search for the word "flash". Tell me if flashplugin-installer is installed(has a green filled in box by it). If it's green, then it's installed.

---

### Post by GumpTron on 2009-07-21
> **Temposs said:**
> What I'd like you to do is open Synaptic Package Manager through the System->Administration menu. Then, press Ctrl-F and search for the word "flash". Tell me if flashplugin-installer is installed(has a green filled in box by it). If it's green, then it's installed.

it is installed and is gree. so is installer and non-free

its strange that i can watch youtube video but not videos from [www.redtube.com](www.redtube.com) or [www.tube8.com](www.tube8.com)

---

### Post by Temposs on 2009-07-21
Please don't link porn sites on the forums. If you are having trouble with your flash player, find a non-porn site to link to for testing.

---

### Post by GumpTron on 2009-07-21
> **Temposs said:**
> Please don't link porn sites on the forums. If you are having trouble with your flash player, find a non-porn site to link to for testing.

ok sorry about that. other than youtube and those porn sites i dont really watch video. what other sites should i test?

---

### Post by Crunchy the Headcrab on 2009-07-21
open a terminal.  It should be under Applications and either in system or accesories.  Type:
> uname -r
Then paste what it says here.

The reason that videos on other sites might not be working is because they may be using another form of video rather than flash.  Let's get your flash problems sorted out first and then work on other formats.  If I were you I would demand that the jack hole that sold it to you for $60 does the work though.

---

### Post by Temposs on 2009-07-21
A good site on which to test flash is [www.hulu.com](www.hulu.com)
Or maybe [www.pandora.com](www.pandora.com)

---

### Post by ralphmcknight on 2009-09-04
i have finally got this working: :-) by comparing 2 systems and finding the difference, as flash / shockwave worked on one and not the other!
anyway, the solution for me was to remove the following:

libswfdec-0.8-0
swfdec-gnome
swfdec-mozilla

these can easily be removed by going into 
system / admin / synaptic package manager.

once these are removed everything may start to work, if it doesnt, remove all the adobe packages ysing the package manager again, then go to the adobe main site and download flash again, i think its the 8.04+ .deb version, just click on the link on their site.  You can then update to a later version, via the package manager again if you like.

the version of shockwave will then show as shockwave flash 10.0 r22.
you can see this in firefox browser / tools / add-ons, in the plugins tab.

then all will work, including tube8.

---

