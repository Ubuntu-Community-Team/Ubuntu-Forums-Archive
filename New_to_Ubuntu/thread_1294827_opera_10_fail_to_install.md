---
title: "opera 10 fail to install"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by bonez4ever on 2009-10-18
Hi guys .... um i tried downloading and installing opera web browser so I then went to add/or remove programs and type opera and doesn't appear

help me, please

-Bonez4ever

---

### Post by halitech on 2009-10-18
how di dyou try to install it and what file did you download?

---

### Post by bonez4ever on 2009-10-18
I  downloaded the tar.bz2 and tar.gz both cannot be found under the add/ or remove programs and I extracted it also

---

### Post by halitech on 2009-10-18
thats why, add/remove simply looks in the repo for files, not downloaded tarballs. Why not simply download the prepackaged deb file for ubuntu?

[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by Rytron on 2009-10-18
Hello.

Try this:

Download deb package from[ www.opera.com/browser/download/?custom=yes]("www.opera.com/browser/download/?custom=yes")

```
sudo dpkg -i opera_10.00.4585.gcc4.qt3_i386.deb
```

Install flash plugin using the following command
```
sudo apt-get install flashplugin-nonfree
```

If you have problem with your videos follow this procedure
Open Opera
Tools -> Preferences -> advanced tab
Click on Downloads on the left side
find the one that says application/x-shockwave-flash
Click Edit at the bottom it says Use Plugin from the pull down menu
select the one that says: ‘Shockwave Flash – /usr/lib/mozilla/plugins/flashplugin-alternative.
so’ if it doesn’t work you can try a different one from the pull down menu
Click OK and exit

Install Java plugins using the following command
```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin ubuntu-restricted-extras
```

---

### Post by sandyd on 2009-10-18
> **bonez4ever said:**
> I  downloaded the tar.bz2 and tar.gz both cannot be found under the add/ or remove programs and I extracted it also
run this in the terminal
```

kdesudo kate /etc/apt/sources.list

```add this to the bottom (on a new line)
```

deb http://deb.opera.com/opera/ etch non-free

```click save.

then copy and paste the rest of the commands to the terminal
```

wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install opera

```WAITTT!!!
almost forgot codecs
```

sudo apt-get install ubuntu-restricted-extras faac faad
```

---

### Post by bonez4ever on 2009-10-18
It keeps asking for my password Carlee and I type it in and it says it incorrect:confused:

---

### Post by halitech on 2009-10-18
> **carlee said:**
> run this in the terminal
```

sudo gedit /etc/apt/sources.list

```add this to the bottom (on a new line)


just to point out, when using graphical apps, you should use gksudo and not sudo

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> Why is it an issue?
Well, to be perfectly honest, most of the time it isn't. For a lot of applications, you can run them the improper way—using sudo for graphical applications and see no adverse side effects.

1. There are other times, though, when side effects can be as mild as Firefox extensions not sticking or as extreme as as not being able to log in any more because the permissions on your .ICEauthority changed. You can read a full discussion on the issue here.

These errors occur because sometimes when sudo launches an application, it launches with root privileges but uses the user's configuration file. 

---

### Post by sandyd on 2009-10-18
> **bonez4ever said:**
> It keeps asking for my password Carlee and I type it in and it says it incorrect:confused:
awwwww......
noooooooooo.
another user forgetting their password..................

---

### Post by halitech on 2009-10-18
> **bonez4ever said:**
> It keeps asking for my password Carlee and I type it in and it says it incorrect:confused:

if you have forgotten your password (are you in the sudo list?) and need to reset it, see here

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by sandyd on 2009-10-18
> **halitech said:**
> just to point out, when using graphical apps, you should use gksudo and not sudo

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
ackkkk....
i saw that bulliten a while ago.
it seems that half of the time, my posts end up with sudo, while the rest go on with gksudo....

hard to teach old dog new tricks ya  know.

post corrected.

---

### Post by halitech on 2009-10-18
> **carlee said:**
> ackkkk....
i saw that bulliten a while ago.
it seems that half of the time, my posts end up with sudo, while the rest go on with gksudo....

hard to teach old dog new tricks ya  know.

post corrected.

I know what you mean, I found it hard to do it correctly as well when I first found out the difference

---

### Post by bonez4ever on 2009-10-18
Thanks guys got my new password and I am now typing in Carlee's code

---

### Post by bonez4ever on 2009-10-18
Ok Carlee's code asks for my password gave it, it accepts it, then it wants me to install gksu, so I install it with the code given I then type in gksudo gedit/etc/apt/source.list and asks me another gksudo install. So I then decided to forget it and  click the .deb link you provided. Well it failed to download saying "The file                                                                                              [http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb](http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb) is a binary, saving it will result in a corrupt file." OI! please help me

---

### Post by Jean-Danjou on 2009-10-18
I was trying to run Opera 10 without success on Jaunty, after installing from synaptique package. I gave up on it, move to Karmic, to find out that Opera wasn't in the synaptic any more! So, something wrong with Opera 10 and Karmic...On top of that, Firefox keep on crashing, so I still looking a decent Browser! Suggestions?

---

### Post by bonez4ever on 2009-10-18
> **Jean-Danjou said:**
> I was trying to run Opera 10 without success on Jaunty, after installing from synaptique package. I gave up on it, move to Karmic, to find out that Opera wasn't in the synaptic any more! So, something wrong with Opera 10 and Karmic...On top of that, Firefox keep on crashing, so I still looking a decent Browser! Suggestions?
:P Join the  club, looks like I am not the only one with some problems installing it.

---

### Post by deancasino on 2009-10-18
> **carlee said:**
> awwwww......
noooooooooo.
another user forgetting their password..................

I'm not envious lol

---

### Post by sandyd on 2009-10-18
> **bonez4ever said:**
> Ok Carlee's code asks for my password gave it, it accepts it, then it wants me to install gksu, so I install it with the code given I then type in gksudo gedit/etc/apt/source.list and asks me another gksudo install. So I then decided to forget it and  click the .deb link you provided. Well it failed to download saying "The file                                                                                              [http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb](http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb) is a binary, saving it will result in a corrupt file." OI! please help me
WAIT!!!!
are you using Kubuntu?

silly me
replace gksudo with kdesudo

sorry 'bout that.

gksudo is for gnome, not kde.......](*,)

---

### Post by bonez4ever on 2009-10-18
Thank you Carlee I am trying that now

---

### Post by bonez4ever on 2009-10-18
I type in kdesudo instead and a new window pops up saying "Kdesudo command not found!"

---

### Post by sandyd on 2009-10-18
> **bonez4ever said:**
> I type in kdesudo instead and a new window pops up saying "Kdesudo command not found!"
for got to mention that you replace gksudo with kdesudo IN THE COMMAND.
which means 
```

gksudo gedit /etc/apt/sources.list
```should look like

```

kdesudo kwrite /etc/apt/sources.list

```

edit: also changed gedit to kwrite becasue gedit isn't avalible in KDE systems.

---

### Post by bonez4ever on 2009-10-18
> **carlee said:**
> for got to mention that you replace gksudo with kdesudo IN THE COMMAND.
which means 
```

gksudo gedit /etc/apt/sources.list
```should look like

```

kdesudo kwrite /etc/apt/sources.list

```

edit: also changed gedit to kwrite becasue gedit isn't avalible in KDE systems.
oh, I wrote it with gedit, let's try again.... and thank you for your patience

---

### Post by bonez4ever on 2009-10-18
I copied and pasted your code " kdesudo kwrite /etc/apt/sources.list" and it still says " Kdesudo command not found!
-by the way whats with the beans under my Name?

---

### Post by sandyd on 2009-10-18
> **bonez4ever said:**
> oh, I wrote it with gedit, let's try again.... and thank you for your patience
unfortunately, i have a kubuntu/gnome mixed system so i currently have nooo idea what text editor that installed on kubuntu by default.
could someone tell me?

---

### Post by bonez4ever on 2009-10-18
> **carlee said:**
> unfortunately, i have a kubuntu/gnome mixed system so i currently have nooo idea what text editor that installed on kubuntu by default.
could someone tell me?
Well it says " Kate Text Editor " don't know if that helps you.

---

### Post by sandyd on 2009-10-18
> **bonez4ever said:**
> I copied and pasted your code " kdesudo kwrite /etc/apt/sources.list" and it still says " Kdesudo command not found!
-by the way whats with the beans under my Name?
maybe
kdesudo kate /etc/apt/sources.list

ok, i give up and im gonna do this the stupid way that you should not do on a regular basis.
```

sudo kate /etc/apt/sources.list

```

---

### Post by bonez4ever on 2009-10-18
> **carlee said:**
> maybe
kdesudo kate /etc/apt/sources.list

ok, i give up and im gonna do this the stupid way that you should not do on a regular basis.
```

sudo kate /etc/apt/sources.list

```
K, I am going to upload a  screen shot so  you can see it for your self, because it's still doing the same thing.

---

### Post by sandyd on 2009-10-18
> **bonez4ever said:**
> K, I am going to upload a  screen shot so  you can see it for your self, because it's still doing the same thing.
i meant try this command
sudo kate /etc/apt/sources.list

not the kdesudo one.

---

### Post by bonez4ever on 2009-10-18
> **carlee said:**
> i meant try this command
sudo kate /etc/apt/sources.list

not the kdesudo one.
Take a look... [[IMG]http://img4.imageshack.us/img4/4469/snapshot2vg.th.jpg[/IMG]](http://img4.imageshack.us/i/snapshot2vg.jpg/)

---

### Post by sandyd on 2009-10-18
> **bonez4ever said:**
> Take a look... [[IMG]http://img4.imageshack.us/img4/4469/snapshot2vg.th.jpg[/IMG]]("http://img4.imageshack.us/i/snapshot2vg.jpg/")
i think im cursed.

```

sudo nano /etc/apt/sources.list

```scroll down to the bottom with your arrow keys, then hit enter on the line and paste the stuff i said to paste on post#6

and ill give a list of stuff to run in the terminal.
just tell me which ones open
```

kpackagekit

```
```

synaptic

```

---

### Post by igknighted on 2009-10-18
> **bonez4ever said:**
> Ok Carlee's code asks for my password gave it, it accepts it, then it wants me to install gksu, so I install it with the code given I then type in gksudo gedit/etc/apt/source.list and asks me another gksudo install. So I then decided to forget it and  click the .deb link you provided. Well it failed to download saying "The file                                                                                              [http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb](http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb) is a binary, saving it will result in a corrupt file." OI! please help me

Right click the link at the bottom of this post, then save-as.  Now you can click on the file in the location you save it to and it will install.

Although, fwiw, there is a qt4 version of Opera which you should use instead of the qt3 version (qt4 is a newer/better version of qt3, these are the libraries that opera uses to draw the windows on your screen).  Which begs the question, is qt3 even installed by default anymore?

qt4 version (try first): [http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt4_i386.deb](http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt4_i386.deb)

qt3 version (if above fails): [http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb](http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb)

---

### Post by bonez4ever on 2009-10-18
> **igknighted said:**
> Right click the link at the bottom of this post, then save-as.  Now you can click on the file in the location you save it to and it will install.

Although, fwiw, there is a qt4 version of Opera which you should use instead of the qt3 version (qt4 is a newer/better version of qt3, these are the libraries that opera uses to draw the windows on your screen).  Which begs the question, is qt3 even installed by default anymore?

qt4 version (try first): [http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt4_i386.deb](http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt4_i386.deb)

qt3 version (if above fails): [http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb](http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb)
Hey buddy it's not working [[IMG]http://img4.imageshack.us/img4/7599/snapshot3bh.th.jpg[/IMG]](http://img4.imageshack.us/i/snapshot3bh.jpg/)

---

### Post by igknighted on 2009-10-18
Also, for those giving the debian etch repo... why not have him/her use the graphical software sources interface?  Might make this much easier... I don't have a recent Kubuntu installed at the moment otherwise I'd post some instructions on that.

---

### Post by igknighted on 2009-10-18
> **bonez4ever said:**
> Hey buddy it's not working [[IMG]http://img4.imageshack.us/img4/7599/snapshot3bh.th.jpg[/IMG]](http://img4.imageshack.us/i/snapshot3bh.jpg/)

You need to right click and save link as, you can't actually click the link itself.

---

### Post by sandyd on 2009-10-18
> **igknighted said:**
> Also, for those giving the debian etch repo... why not have him/her use the graphical software sources interface?  Might make this much easier... I don't have a recent Kubuntu installed at the moment otherwise I'd post some instructions on that.
i **think** kpackagekit

@OP
can press ALT+F2 and enter in
```

kpackagekit

```

hit enter

---

### Post by sandyd on 2009-10-18
> **igknighted said:**
> You need to right click and save link as, you can't actually click the link itself.
and clicking the link should work [ see screenshot ], just tried it. which is why im about to ask what version of ubuntu hes using and if hes installed all the updates.

---

### Post by igknighted on 2009-10-18
@OP:

If you can't right click the link,  try this command in the konsole/terminal:

```
wget http://ftp.ussg.iu.edu/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt4_i386.deb
```

After it is done, the file should be in your home folder, and you can click it to install it.

---

### Post by bonez4ever on 2009-10-18
Didn't work, however I was able to download it and somewhat install it [[IMG]http://img199.imageshack.us/img199/7950/snapshot4tr.th.jpg[/IMG]](http://img199.imageshack.us/i/snapshot4tr.jpg/)
and thank you once again for not giving  up.Oh! and  to answer Carlee's question I have all the updates except for 4 of them ,but there's also a problem with them too as soon as I install them they come right back asking to install them again,and again, and again you get the point.

---

### Post by bonez4ever on 2009-10-19
Bump...

---

### Post by sandyd on 2009-10-19
> **bonez4ever said:**
> Bump...
i don't think im cursed today, so.....
```

sudo apt-get upgrade
```
there seems to be a problem on my side too. same thing is happening and its annoying me....

---

### Post by bonez4ever on 2009-10-19
> **carlee said:**
> i don't think im cursed today, so.....
```

sudo apt-get upgrade
```
there seems to be a problem on my side too. same thing is happening and its annoying me....
Well thanks for helping me I appreciate it:)

---

