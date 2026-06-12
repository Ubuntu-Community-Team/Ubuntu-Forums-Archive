---
title: "Noob ?'s"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by D1Knight on 2009-10-30
O.K. here is my Noob ?'s:  

1. What is jackass.canonical.com and something with the word "rookery"?    Are these legit servers?  
2. Why am I having slow download speeds from Canonical/Ubuntu servers (September-October)?  
3. Where and what do I check to find out if I have been hacked?  
4. Is my puter a zombie (not a joke, either)?   Thank you for any and all help.Peace.   

*More* 5. I am using 0.01% of SWAP, but have not even got close to 100% use of RAM. What does this mean?  Thanks.

---

### Post by themusicalduck on 2009-10-30
1. Not sure what it is exactly, but anything with canonical.com on the end of it can probably be assumed to be hosted by canonical.

2. The download speeds will be slow because 9.10 has just been released and the servers are busy as people are upgrading. Are you updating or are you downloading an iso? If you are downloading an iso then you're better off using the torrents. If you're updating then you can select a faster mirror under System > Administration > Software Sources. Click other from the 'Download from:' dropdown menu and then press the Select Best Server button.

3. No idea.

4. :S

5. Swap is more likely to be used if you're ram is closer to 100%, but it has other uses as well. Basically it's most likely working fine. How much swap space do you have?

---

### Post by fancypiper on 2009-10-30
Install and run chkrootkit

sudo apt-get install chkrootkit
sudo chkrootkit

---

### Post by earthpigg on 2009-10-30
> **D1Knight said:**
> O.K. here is my Noob ?'s:  1. What is jackass.canonical.com and something with the word &quot;rookery&quot;?    Are these legit servers?  2. Why am I having slow download speeds from Canonical/Ubuntu servers (September-October)?  3. Where and what do I check to find out if I have been hacked?  4. Is my puter a zombie (not a joke, either)?   Thank you for any and all help.Peace.   *More* 5. I am using 0.01% of SWAP, but have not even got close to 100% use of RAM. What does this mean?  Thanks.

1. system -> admin -> software sources -> download from. anything you find there is legit.

2. because everyone is downloading 9.10 right now, so the servers are slammed. in system -> admin -> software sources, you can have it test all the different mirrors to find the fastest server. i am getting my ISP's max down at the moment.

3. what makes you think you have?

4. what makes you think it is?

5. this is normal, worry not. a swap partition still has a filesystem, and even an 'empty' filesystem (ext3, swap, ntfs, whatever) always has a bit of space used for the filesystem's table of contents and whatnot. that 0.01% of use is the swap partition's information that says "I am a swap partition! use me if you need to!" to Ubuntu.



if you think there is something funny with your repos, post the output of this command please and we will take a look:
```

cat /etc/apt/sources.list
```

(or open that in your fav word processor/text editor and copy/paste it here)

---

### Post by Lazy-buntu on 2009-10-30
Vets correct me if I'm wrong, but swap is usually used when hibernating or if your RAM is close to 100% usage.

---

### Post by sandyd on 2009-10-30
> **D1Knight said:**
> O.K. here is my Noob ?'s:  1. What is jackass.canonical.com and something with the word &quot;rookery&quot;?    Are these legit servers?  2. Why am I having slow download speeds from Canonical/Ubuntu servers (September-October)?  3. Where and what do I check to find out if I have been hacked?  4. Is my puter a zombie (not a joke, either)?   Thank you for any and all help.Peace.   *More* 5. I am using 0.01% of SWAP, but have not even got close to 100% use of RAM. What does this mean?  Thanks.
1. Thats a redirection to the main repos, [http://archive.ubuntu.com](http://archive.ubuntu.com)

---

### Post by D1Knight on 2009-10-30
> **themusicalduck said:**
> 1. Not sure what it is exactly, but anything with canonical.com on the end of it can probably be assumed to be hosted by canonical.

2. The download speeds will be slow because 9.10 has just been released and the servers are busy as people are upgrading. Are you updating or are you downloading an iso? If you are downloading an iso then you're better off using the torrents. If you're updating then you can select a faster mirror under System > Administration > Software Sources. Click other from the 'Download from:' dropdown menu and then press the Select Best Server button.

3. No idea.

4. :S

5. Swap is more likely to be used if you're ram is closer to 100%, but it has other uses as well. Basically it's most likely working fine. How much swap space do you have?

 @2-I should have been more clear. I downloaded Ubuntu 9.10 ISO on 10-29-09 It took less than 15 minutes. It appears the problem has more to do with the repositories of Ubuntu (slow since September 2009). Everything else downloads fast-normal. 
  @5-Swap is 5.7GB (default install) and RAM is 2GB.   Thanks for you help/ideas.Peace

---

### Post by D1Knight on 2009-10-30
> **fancypiper said:**
> Install and run chkrootkit

sudo apt-get install chkrootkit
sudo chkrootkit

  Fancypiper,  I did and it checked out-clean.  Thank you.Peace

---

### Post by D1Knight on 2009-10-30
> **earthpigg said:**
> 1. system -> admin -> software sources -> download from. anything you find there is legit.

2. because everyone is downloading 9.10 right now, so the servers are slammed. in system -> admin -> software sources, you can have it test all the different mirrors to find the fastest server. i am getting my ISP's max down at the moment.

3. what makes you think you have?

4. what makes you think it is?

5. this is normal, worry not. a swap partition still has a filesystem, and even an 'empty' filesystem (ext3, swap, ntfs, whatever) always has a bit of space used for the filesystem's table of contents and whatnot. that 0.01% of use is the swap partition's information that says &quot;I am a swap partition! use me if you need to!&quot; to Ubuntu.



if you think there is something funny with your repos, post the output of this command please and we will take a look:
```

cat /etc/apt/sources.list
```(or open that in your fav word processor/text editor and copy/paste it here)

  @1-Thanks, that helps to confirm.   
@2-@2-I should have been more clear. I downloaded Ubuntu 9.10 ISO on 10-29-09 It took less than 15 minutes. It appears the problem has more to do with the repositories of Ubuntu (slow since September 2009). Everything else downloads fast-normal.   
@3-See @2 response (slow repository downloads since September)   
@4-Same as @3-See @2   
@5-Woa, thanks thats makes it a lot clearer.      


# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to # newer versions of the distribution.  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted  ## Major bug fix updates produced after the final release of the ## distribution. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team. Also, please note that software in universe WILL NOT receive any ## review or updates from the Ubuntu security team. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  ## team, and may not be under a free licence. Please satisfy yourself as to  ## your rights to use the software. Also, please note that software in  ## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse  ## Uncomment the following two lines to add software from the 'backports' ## repository. ## N.B. software from this repository may not have been tested as ## extensively as that contained in the main release, although it includes ## newer versions of some applications which may provide useful features. ## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse  ## Uncomment the following two lines to add software from Canonical's ## 'partner' repository. ## This software is not part of Ubuntu, but is offered by Canonical and the ## respective vendors as a service to Ubuntu users. # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by D1Knight on 2009-10-30
> **carlee said:**
> 1. Thats a redirection to the main repos, [http://archive.ubuntu.com](http://archive.ubuntu.com)

  Thank you.P

---

### Post by earthpigg on 2009-10-31
> **D1Knight said:**
> > 1. Thats a redirection to the main repos, [http://archive.ubuntu.com](http://archive.ubuntu.com)Thank you.P

and using those main repos is why you are having slow speeds when installing stuff. read what i said above about the main servers being slammed -- it applies to the main software repository servers too... and archive.ubuntu.com is the main *main* ***main*** repository.

you are sharing bandwidth with 5,000,000 other people around the world that all just installed 9.10 and are now downloading/installing their favorite apps and games and whatnots.

system -> admin -> software sources -> download from -> drop down menu -> "other" -> find best server.

it will test them all (there are several hundred) and find the quickest one at the moment. right now, it will not be anything with ubuntu.com or canonical.com in the name. it will probably be some obscure university or something. that's fine, if ubuntu didn't trust them they wouldn't have listed them. and which is the quickest will change over time, as more or fewer people use or do not use a given server or set of servers.

---

### Post by D1Knight on 2009-10-31
> **earthpigg said:**
> and using those main repos is why you are having slow speeds when installing stuff. read what i said above about the main servers being slammed -- it applies to the main software repository servers too... and archive.ubuntu.com is the main *main* ***main*** repository.

you are sharing bandwidth with 5,000,000 other people around the world that all just installed 9.10 and are now downloading/installing their favorite apps and games and whatnots.

system -> admin -> software sources -> download from -> drop down menu -> "other" -> find best server.

it will test them all (there are several hundred) and find the quickest one at the moment. right now, it will not be anything with ubuntu.com or canonical.com in the name. it will probably be some obscure university or something. that's fine, if ubuntu didn't trust them they wouldn't have listed them. and which is the quickest will change over time, as more or fewer people use or do not use a given server or set of servers.
[SIZE=2][B]
[COLOR=Purple]Earthpigg, thanks a bunch!:D I get what you are saying and I followed your instructions, I'll keep an eye on it next time I have an update to do. ;) The main issue I had was, from about May 2009 till begin of September 2009 downloads from repositories was nice and smooth. Starting in mid-September until now, very slow.:(

Like you were explaining, paraphrase-if a lot of people are using the "default" servers, it will eventually become a lot slower.

Much appreciated your help. \\:D/I am learning thankfully.:) You have a great weekend and week!=D> P.
[/COLOR][/B][/SIZE]

---

