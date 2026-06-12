---
title: "whats the difference in gnome and kde...if"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by AXeS on 2009-04-15
i connect to the net via mobile phone.

in windows it works fine,in ubuntu,why do i have to struggle?
i installed kubuntu last nighu and my mobile connects, better than windows.

what does kubuntu (kde) have that ubuntu (gnome) dont have?

im not dissing linux or anything im just stating something...i think it was said before. 
if things are made easy in ubuntu then why do i have to post a question trying to solve the easy stuff, and then the answers i get is astounding. im not exactly a newb but if i was and if i hated complexities i would have just gone back to windows and stick it out because atleast i know it will work.

im trying to fully use linux and at 1st ubuntu got me hooked,i love it,but the simple things just dont want to work and getting answers takes time i know,but what if you tried 4 different ways and it still dont work.


so... why would my phone connect on kubuntu so easily but in ubuntu it cant.

---

### Post by slibuntu on 2009-04-15
KDE and Gnome are different desktops that you can run on top of ubuntu. 

Ubuntu comes preinstalled with Gnome, while Kubuntu comes with KDE

[KDE]("http://www.kde.org/")
[Gnome]("http://gnome.org")

---

### Post by t.rei on 2009-04-15
> **AXeS said:**
> 
so... why would my phone connect on kubuntu so easily but in ubuntu it cant.

Actually without any information from your side that is hard to answer:
What hardware, what kernel?

My guess would be that you run something linke kubuntu 8.10 and ubuntu 9.04. Yes, sometimes things break. Maybe it's the other way around? 

I'd check the kernel versions on those systems
```

uname -r

```

---

### Post by kwacka on 2009-04-15
deleted

---

### Post by AXeS on 2009-04-15
> **slibuntu said:**
> KDE and Gnome are different desktops that you can run on top of ubuntu. 

Ubuntu comes preinstalled with Gnome, while Kubuntu comes with KDE

[KDE]("http://www.kde.org/")
[Gnome]("http://gnome.org")


i understand that, thanx for pointing it out.

i just put that there so it can be a bit clearer to understand my question.
and still what would kubuntu have that ubuntu already not have.

---

### Post by theozzlives on 2009-04-15
Kubuntu is Ubuntu only with KDE, maybe that destop supports things that GNOME don't. Like I like the network interface in GNOME better than KDE.

---

### Post by AXeS on 2009-04-15
> **t.rei said:**
> Actually without any information from your side that is hard to answer:
What hardware, what kernel?

My guess would be that you run something linke kubuntu 8.10 and ubuntu 9.04. Yes, sometimes things break. Maybe it's the other way around? 

I'd check the kernel versions on those systems
```

uname -r

```


running both Ubuntu 8.10, kubuntu 8.10. the kernel used as the install no updates (because i cant update ubuntu).

i posted several mobile phone to net connection posts... one that stuck out was, it should just work -thats not an answer i can use- another said i should use wvdial and edit the wvdial.conf accordingly -which i did and redid and redid and searched again and redid,not a solution worth messing a month around with-
anothe said wvdial cant be used -that just confused me-
the last resort i tried was gnome-ppp (manually downloaded and installed) but just doesnt seem to give a solution i was looking for so what i did was ...so last night i installed from a live kubuntu CD i had but didnt like and plugged my phone in put the settings in and... wow it worked? how would it be that it cant connect in ubuntu and how can it be simple when it becomes so complicated.

here are my posts 
[ 1st POST]("http://ubuntuforums.org/showthread.php?t=1116815") NO ANSWER
[ 2nd POST]("http://ubuntuforums.org/showthread.php?t=1120510") GOT MIXED ANSWERS
[ 3rd POST]("http://ubuntuforums.org/showthread.php?t=1122169") GOOD LEADS NO ANSWERS


anyway whats upsetting me isnt just that, i wana use ubuntu and get to know the tweaks, and im getting good at it but if i cant connect how do i find out the problem?

how do i know what to do to fix it... as if im a new user,and if not advanced is fine but it should be fullproof (settings/configs that work) nomatter how advancf.
im determined to fix this.

so, you may search other posts for more details. im using a w810i vodacom network and this is my only connection to the net,im not gona type out what i did already especialy since im using OPERA MINI right now.

---

### Post by Eskaybeast on 2009-04-15
i am a newbie ...So on the 7th day god created human and they werent ubuntu ...Ive got a nokia n70 would like to run a connection but do not have the no how does anyone out there know

---

### Post by AXeS on 2009-04-15
> **slibuntu said:**
> KDE and Gnome are different desktops that you can run on top of ubuntu. 

Ubuntu comes preinstalled with Gnome, while Kubuntu comes with KDE

[KDE]("http://www.kde.org/")
[Gnome]("http://gnome.org")


Tell me is this an idea... i re-install ubuntu 8.10 (fresh install) 
manually download knetwork-manager with it's dependencies and all (whatever the manager is in kubuntu)
then try to connect my phone again? Would that work.
i think it should but what you guys think?

---

### Post by AXeS on 2009-04-15
> **Eskaybeast said:**
> i am a newbie ...So on the 7th day god created human and they werent ubuntu ...Ive got a nokia n70 would like to run a connection but do not have the no how does anyone out there know

we can sort this out tonight ok.

---

### Post by abn91c on 2009-04-15
> **AXeS said:**
> Tell me is this an idea... i re-install ubuntu 8.10 (fresh install) 
manually download knetwork-manager with it's dependencies and all (whatever the manager is in kubuntu)
then try to connect my phone again? Would that work.
i think it should but what you guys think?
you probably dont need to do all that, but anyways the kubuntu net manager is called knetworkmanager

---

### Post by AXeS on 2009-04-15
> **abn91c said:**
> you probably dont need to do all that, but anyways the kubuntu net manager is called knetworkmanager

ok i wont do it unless you got a solution thats fullproof?
i hope you got 1!

---

### Post by mbzn on 2009-04-15
my personal experience, my brother n70 worked fine in Ubuntu8.10 from the first start.
your phone should be a network on its own, see that it has 'usb network' or somthing like that, it should be on auto... i suggest that you play with the settings a little bit. i had this problem with my phone and after a wile i got it to work, dont ask me how though.
You can try installing kubuntu and the install the gnome desktop over that. i think it might be easyer.

---

### Post by Eskaybeast on 2009-04-16
> **mbzn said:**
> my personal experience, my brother n70 worked fine in Ubuntu8.10 from the first start.
your phone should be a network on its own, see that it has 'usb network' or somthing like that, it should be on auto... i suggest that you play with the settings a little bit. i had this problem with my phone and after a wile i got it to work, dont ask me how though.
You can try installing kubuntu and the install the gnome desktop over that. i think it might be easyer.
Thanks man i can only try it 2nite i had something like that but then i didnt read further or tweak the settings . I hav one question for anyone reading this if this doesnt work why do i have to install another distro . To me it seams counterproductive at the end of the day i mite hav 4 distro just 2 do various thngs . Further more 62.3% of humans do not have a internet connection then with al do respect wouldnt linux suck just as much as windows

---

### Post by AXeS on 2009-04-16
> **Eskaybeast said:**
> Thanks man i can only try it 2nite i had something like that but then i didnt read further or tweak the settings . I hav one question for anyone reading this if this doesnt work why do i have to install another distro . To me it seams counterproductive at the end of the day i mite hav 4 distro just 2 do various thngs . Further more 62.3% of humans do not have a internet connection then with al do respect wouldnt linux suck just as much as windows

windows dont suck windows is good ...

just not in this lifetime.

I think if people kept their windows clean they would have a better vision of things. Besides i think clean windows is just to look through.

---

