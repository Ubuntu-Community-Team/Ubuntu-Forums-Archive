---
title: "Simple and EASIEST way to install PIDGIN on ubuntu?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by rajm11 on 2009-12-16
hello all
I am not new to ubuntu but not quite into it like all you are, I m ajust an avrage user. But ubuntu satisfies my work needs in every which way.
However from many days i was trying to use pidgin as my messenger, with version 2.5.2 but to no avail it wont connect to yahoo, Had problem connecting gmail as well. 
Then while searching i read that Pdgin old version does not log into yahoo , we have to have new version. 
So off I went 
Trying to uninstall pidgin from ADD remove wont work, I headed to package manager, and uninstalled it. HOWEVer pidgins new version was still 2.5.2 in there,so some how I forced VErsion and now have new listed.
BUT
when i try to click and mark it for installation, and lcick apply
here is what I get 

pidgin:
 Depends: libpurple0 but it is not going to be installed
  Depends: perl (>=5.10.0-11.1ubuntu2.3) but 5.10.0-11.1ubuntu2 is to be installed
 Recommends: pidgin-libnotify but it is not going to be installed

somw ehre i read u have to remove ur libpurpl0 totally and they had this command and so i did it and well it dosent budge.

can any one tell me how to resolve this?
a step by step for layman. please

---

### Post by Soul-Sing on 2009-12-16
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```

```
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

```
sudo apt-get update
```

```
sudo apt-get install pidgin
```

[COLOR="Red"]edit!: simple way to install the newest version....[/COLOR]

---

### Post by rajm11 on 2009-12-16
okay I tried this all step by step and this is what i got again now in terminal 

The following packages have unmet dependencies:
  pidgin: Depends: libpurple0 (>= 1:2.6.0) but it is not going to be installed
          Depends: perl (>= 5.10.0-11.1ubuntu2.3) but 5.10.0-11.1ubuntu2 is to be installed
E: Broken packages
is there any other messenger which include bith yahoo ang google in it ? I tried ayttm but it does not have google chat in it besides its entry in reposiory is older than the version on website.
oh and thanks for trying to solve so fast.

---

### Post by Soul-Sing on 2009-12-16
Please try synaptic package manager: on the left corner: search for broken packages: mark them and try to reinstall them.

Or you could try a force install of libpurple0.

---

### Post by rajm11 on 2009-12-16
oka tried as u said, tried to install pidgin again, and then from left hand side gone to custom filetrs>> broken,, well there is nothing there, I installed kopete but that dosent get online I dont know why, it just says connection error, Is there ANY working messenger for Ubuntu ? a simple one

---

### Post by twright on 2009-12-16
If you are on the latest version of Ubuntu (9.10) the default messenger is Empathy, not Pidgin which supports Yahoo (etc.) and should work well. If you are on an older version of Ubuntu you can either upgrade or install Empathy by clicking [here]("apt:empathy").

---

### Post by rajm11 on 2009-12-16
thank you twilight,I will certianly try that, but as i was saying, I tried force instlal lilpurple0 then i got another dependency called perl with ubunt 2.3,its like I am in dependecy hell.........

---

### Post by rajm11 on 2009-12-16
NOPE, even empathy is like not worthy, first it has NO yahoo in it, and then I tried to access gtalk, but it still to connect,geez,is there a decent and simplest one,I would say go for web ones now if ur on ubuntu! btw its ubuntu 8.10

---

### Post by Paul T. on 2009-12-16
Try this link [http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)
Works for me:P

---

### Post by twright on 2009-12-16
> **rajm11 said:**
> NOPE, even empathy is like not worthy, first it has NO yahoo in it, and then I tried to access gtalk, but it still to connect,geez,is there a decent and simplest one,I would say go for web ones now if ur on ubuntu! btw its ubuntu 8.10

Empathy works fine with my Google Talk (you have to put in the full address as googlemail.com though). It also has Yahoo support. Of course the version in 8.10 might vary a lot (empathy had only just been released then).

---

### Post by rajm11 on 2009-12-16
okay only problem is I dont have pidgin, I removed old version to install new one, and now :(

---

### Post by rajm11 on 2009-12-16
okay, that is weird! see this and oh yah it still hasnt logged in google, i tried with gmail.com and with googlemail.com too now as u said.

---

### Post by Merk42 on 2009-12-16
Anything pre 9.04 or even 9.10 of Empathy was really lacking.

The [link Paul T posted](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml) is probably your best bet.
You could even use the version of Pidgin in the default repositories if you scroll down to "alternate method" on that link

---

### Post by rajm11 on 2009-12-16
okay, Merk42, see the thing is I removed old pidgin, cause i wanted to install new one, so when i did that some how by reading on forum I was able to force repository to new version on the pidgin, Which is current 2.6.4 but when I try to install that new one its gives me 
pidgin:
 Depends: libpurple0 but it is not going to be installed
  Depends: perl (>=5.10.0-11.1ubuntu2.3) but 5.10.0-11.1ubuntu2 is to be installed
 Recommends: pidgin-libnotify but it is not going to be installed

as the first answer mentions I tried to install libpurple0 forcefully,
but then I got stuck on perl perl (>=5.10.0-11.1ubuntu2.3) but 5.10.0-11.1ubuntu2
which was forfully updated to the version it shows now, i,e. ubuntu2, 
so I need to further down perl 
and well i cant seems to find a way out.
so now I am out of OLD PIDGIn, which hardly connected to yahoo 
and I cant install new one.
:( :(

---

### Post by Merk42 on 2009-12-16
I guess you did the whole ppa thing in the second post?

You could try going to **System > Administration > Software Sources** and taking out the added PPA under **Other Software**

That should reset the most recent pidgin to be the one in the default repos that you uninstalled in the first place.

---

### Post by twright on 2009-12-16
> **rajm11 said:**
> okay, that is weird! see this and oh yah it still hasnt logged in google, i tried with gmail.com and with googlemail.com too now as u said.

Ah, I remember back in the olden' days, Empathy's support for most protocols was shipped separately.

---

### Post by rajm11 on 2009-12-16
yes I have tried mostly each and every step on this thread, but its not working.
and I annother weird thing, I tried to remove that pps from the third part tab, it wont go away, tried it several times, what is going on??? I cant understand it.is this libpurple and PPA not getting outta system is my systems problem ? and tw right, can I install yahoo's protocol in empathy,in a simle way like apt get or something ?
its late for me, but plz do post sugestions, may be something wil work out I will try them and post results tomorrow. 
Thanks all

---

### Post by joes7 on 2009-12-16
Pidgin comes with Xubuntu / Ubuntu. If yours doesn't, you can always download it from

Applications->Add/Remove Applications and search for "pidgin"

---

### Post by rajm11 on 2009-12-17
okay so,as u ppl torld me, I removed the ppa line from the softwre sources, let my computer resst for night, and in morning i was able to install OLD pidgin (2.5.7),addes modification from web site 

[http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)

so it could connect to yahoo, and It did connect, now 
I wanted to upgrade it to new version so, i added ppa line from the method mentioned in this thread and marked pidgin for update when i chose to apply 
this is what i got AGAIN! 

pidgin:
  Depends: pidgin-data (>=1:2.6.4) but 1:2.5.2-0ubuntu1 is to be installed
 Depends: libpurple0 but it is not going to be installed
  Depends: perl (>=5.10.0-11.1ubuntu2.3) but 5.10.0-11.1ubuntu2 is to be installed
 Recommends: pidgin-libnotify but it is not going to be installed

i dont know, I think i will haveto stick to the old one till 10.04 
but there should be work around dont you think? any one plz?

---

