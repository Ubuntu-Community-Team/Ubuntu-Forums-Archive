---
title: "what is the best way to use partitions"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by tropdoug on 2009-02-06
I wonder if there is either a comprehensive how to, or maybe someone here who might be able to assist. 

I have been using Linux now for a year, and find it fantastic. There is a learning curve for sure, but it's worth it. During my journey I have clean installed each upgrade as it occurred or as I have been brave enough. But one thing I am not clear about is using partitions to there best advantage with Linux.

What I have right now, is a root partition, a separate /home partition, another one for Music on a second drive, (because I need the storage space) and a 320 gig external drive that is my backup. However I have quiet a bit of spare space, and I think I have enough programs for now. 

I have noticed that when I do a clean install of a new kernel, such as the one I did for 8.10 I then have to download and install all the programs that I had before. They keep the same settings because the settings are contained in the ./files in /home. Updates can take ages to download all the packages and even then I find, "oh yeah I forgot that" and so I spend more time downloading.

So I am thinking - is there a way to store all my programs, and the associated files that exist in other directories on seperate partitions and simply upgrade the kernel,  or install just the new kernel version on a small partition. Then all my programs would be there and I could just update as required. 

The problem is I would not know what directories to move, ie /etc/..... /var or whatever and how would I tell the kernel where the files were. Perhaps that is too ambitious?

Anyway if there is advice about organising your partitions and drives for maximum simplicity, protection and usage I would be very interested as would many others I suspect. 

Looking forward to people's thoughts.

---

### Post by indytim on 2009-02-06
A couple of things come to mind among your options:

1.  Since you have adequate storage space, I would recommend building the new version / distro as a separate boot.  Keep your existing "production" ops until all is happy. (I'm currently able to boot to 4 different distro's versions + W2k as part of my boot options).
2.  Checkout aptoncd to assist in the transfer to a new ops.

Hope this helps a bit.

IndyTim

---

### Post by apjone on 2009-02-06
The most recent installed programs (.deb files) can be found in /var/cache/apt/archives/

I am sure if you read up on apt that you would find away to keep all debs downloaded. (even if it is a batch job that copies them to another directory). However different versions on Ubuntu use different versions of the programs, so you will more than likely have to update the program next time you do a apt-get upgrade / auto updqate.

---

### Post by apjone on 2009-02-06
Have used this in the past with multiple Ubuntu Clients on one Network [http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)

---

### Post by hyper_ch on 2009-02-06
I don't really understand what you ask... however the downloaded deb files (trough package manager like synaptic, adept, apt-get, aptitude) are stored in /var/cache/apt/archives

On a same instal (same version of ubuntu and same bitrate [32/64]) you can use those packages again.

You can also use this command to create a list of installed packages:
```

dpkg -l | awk '/ii/ { print $2 }' > packages.txt

```

or this one to create just one line of all the installed apckages:
```

dpkg -l | awk '/ii/ { print $2 }' | tr '\n' ' ' > packages.txt

```

with the latter one you could then reinstall them all by issuing:
```

sudo apt-get install `cat packages.txt`

```

So if you save the deb files in the archive folder, then restore them upon a new installation and then run the "sudo apt-get install `cat packages.txt`" command you will reinstall that all (if you made a list first).

Also you don't have to install all those packages. Some are dependant from others. E.g. you don't need ever single openoffice packages but openoffice.org for example. You can use that list to trim down what is installed and what you want to have installed again. You can install multiple packages just by issuing this:
```

sudo apt-get install PACKAGE1 PACKAGE2 PACKAGE3 PACKAGE4

```
e.g.
```

sudo apt-get install thunderbird firefox openoffice.org gimp vlc ....

```

---

### Post by tnd on 2009-02-06
^^That's pretty nifty. 
Am I right in thinking regular use of the clean/autoclean commands might delete some of those if you're not careful, or am I completely off on what they do?

---

### Post by hyper_ch on 2009-02-06
```
sudo apt-get clean
``` will delete the downloaded .deb files in the archive folder.

---

### Post by tnd on 2009-02-06
Ah ok so avoid doing that if you want to use the above method :)

---

### Post by hyper_ch on 2009-02-06
well, I reinstall every 6 months (upon a release of a new version or in a late alpha) so I don't save the deb packages anyway. Just the list of installed things is important to me :)

---

### Post by tropdoug on 2009-02-06
There are some great suggestions here, thanks all, I think there could be more obviously I was right, there is an interest in this area. 

OK so I understand that if I was to save /var/cache/apt/archives to my /home when I install Jaunty in April (or maybe before) I could use the install commands listed along with the cat command and the new installation would know where the programs are, and what they were, is that correct?

I get the fact that a new version has many updated programs, ie Jaunty comes with OOOrg 3 not 2.4 which is what I have now. So in that case having the 2.4 re loadedwould be dumb. (I am thinking aloud) hmm. 

The default procedure in a new version loads what the developers have decided is required. So if I am a minimalist I could use the building a list of programs to then help me remove what I don't want. (Dependencies allowing of course) 

Ok I think I need to consider this for a while. 

What about I have read that it is good practise to place /var and /opt onto seperate partitions, but don't know why? any explanations to move me along a bit?

---

### Post by hyper_ch on 2009-02-06
the intrepid packages won't work on jaunty. So saving those packages won't do you any good. However you can still save a list of installed apckages so that you then can easily and "quickly" get all your stuff back.

---

### Post by mikechant on 2009-02-06
*What about I have read that it is good practise to place /var and /opt onto seperate partitions, but don't know why? any explanations to move me along a bit?*

/var contains things like logs amd mail spools, which under certain circumstances can grow rapidly and fill the partition. If /var is part of / then this is more likely to make the system unusable. In practice, I get the impression that these problems are rare and most home users do not have a seperate /var.

/opt is supposed to be for 'non-default application software'. I don't have access to my Ubuntu install at present but I believe that things installed as standard packages from the repositories or .debs don't usually get installed here, so you may well have nothing in here. I think *if* you had non-packaged software installed here you could have it on a seperate partition to make it easy to transfer this software to a new release. Again, I think that nearly all home users do not have a seperate /opt.

---

### Post by tropdoug on 2009-02-06
Hyper_ch thanks that is what I suddenly came to realize. and mickechant I think there must be good reasons so I like to try to learn and with you guys to help thats always good. 

I came across this explanation in regard of placing /var and /opt on seperate partitions. Interesting. [http://cfsg.org/programs/education/unix/partitions.html](http://cfsg.org/programs/education/unix/partitions.html)

I shall research some more.

:D  :popcorn:

---

