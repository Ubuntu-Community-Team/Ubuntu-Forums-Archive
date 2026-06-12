---
title: "Ubuntu 10.10"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by mrtsmith on 2011-06-04
Hi all I'm running into difficulties with helping my dad with ubuntu. Currently the hard part is I'm on the west coast , he's in the midwest. But down to the basics any help would be appreciated.

I'm using ubuntu 10.04 lts on a dell. everything is running great. He has ubuntu 10.10 64 bit. I helped him run through the setup through the howtoforge website for setting up ubuntu (since this is what i've done since using ubuntu 8). The main issue he's running into was not being able to install multiple packages such as the medibuntu, for some reason it shows unathenticated like the gpg key isn't there. I tried going directly through medibuntu webpage still having that issue. 

So my main question is one is there a difference between 32 and 64 bit (i can't tell). I tried using remote desktop, apparently you need to be on the same network or vpn. I tried to go through his ip directly through the provider. and lastly just to see if it would work. I opened the port on my side through firestarter, and dmz'd myself on my router and still not able to connect. 

thanks in advance

---

### Post by collisionystm on 2011-06-04
You can't access his computer because he needs to configure port forwarding in his router. What exactly are you trying to get from medubuntu? Have him just install ubuntu tweak. Google it. Best tool ever and will make the old man really happy.

---

### Post by dFlyer on 2011-06-04
> **mrtsmith said:**
> Hi all I'm running into difficulties with helping my dad with ubuntu. Currently the hard part is I'm on the west coast , he's in the midwest. But down to the basics any help would be appreciated.

I'm using ubuntu 10.04 lts on a dell. everything is running great. He has ubuntu 10.10 64 bit. I helped him run through the setup through the howtoforge website for setting up ubuntu (since this is what i've done since using ubuntu 8). The main issue he's running into was not being able to install multiple packages such as the medibuntu, for some reason it shows unathenticated like the gpg key isn't there. I tried going directly through medibuntu webpage still having that issue. 

So my main question is one is there a difference between 32 and 64 bit (i can't tell). I tried using remote desktop, apparently you need to be on the same network or vpn. I tried to go through his ip directly through the provider. and lastly just to see if it would work. I opened the port on my side through firestarter, and dmz'd myself on my router and still not able to connect. 

thanks in advance

Here is a link I found on the forum:

[http://ubuntuforums.org/showthread.php?t=764906](http://ubuntuforums.org/showthread.php?t=764906)

---

### Post by mrtsmith on 2011-06-04
Thanks for the quick response. Basicly I was stating with the medibuntu as we were walking through the howtoforge website we were trying to make ubuntu run like windows work. So the 64 bit ver is not different compared to the 32 bit ver than.

Once again thank for the response. we'll try the ubuntu tweak

---

### Post by ExileAmongYou on 2011-06-04
The command they give on the medibuntu website for setting up the repository should add the gpg key automatically. Is that what you tried?
You just copy and paste this whole command into the terminal and run it in one go.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by collisionystm on 2011-06-04
> **mrtsmith said:**
> Thanks for the quick response. Basicly I was stating with the medibuntu as we were walking through the howtoforge website we were trying to make ubuntu run like windows work. So the 64 bit ver is not different compared to the 32 bit ver than.

Once again thank for the response. we'll try the ubuntu tweak

They are both one and the same. Just extended pieces of code is the only thing that makes the difference

---

### Post by mrtsmith on 2011-06-05
Thanks dlfyer that link worked to help get everything running.

@exileamongyou that link from medibuntu and howtoforge the perfect desktop didn't work.

collisionystm thanks for the verification. I didn't think 64 bit and 32 bit were different..

Hopefully you guys could aid with this. and of course I'm still going to dig around . 

We got everything now install based off "the perfect desktop ubuntu 10.10 mavrick meerkat". 

after he ran cheese he got this error: uvc camera(046d:081d) (/dev/video0) he's currently using a logictech c510.  

btw you all are awesome : Fully appreciate all the help. still trying to learn all this LOL 

This is the error msg he gets after using skype after i gave him the command in terminal mode LD_PRELOAD=/usr/lib32/lib4l/v4lcompat.so skype

"""one additional comment when he doesn't use the ld preload comment he gets no video when he tests..

(This below is the error msg he recieves)
(<unknown>:7493) :  GTK-WARNING **:  /usr/lib/gtk-2.0/2.10.0/imodules/im-bus.so:wrong ELF class: ELFCLASS64

(<unknown>:7493) :   loading IM context type 'ibus' failed 
libv4lconvert: warning more frame sizes then i can handle 


Additionally thanks in advance for any help. I am going to continue to research this as well.

---

