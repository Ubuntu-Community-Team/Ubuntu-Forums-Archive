---
title: "Hamachi in Ubuntu"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by GSI on 2009-08-22
Hello. :) Can you help me? I'm having trouble finding and installing hamachi for ubuntu..

---

### Post by ibutho on 2009-08-22
You could download it from [here]("http://files.hamachi.cc/linux/"). Look at the README files for installation instructions.

---

### Post by scorp123 on 2009-08-22
> **GSI said:**
> Hello. :) Can you help me? I'm having trouble finding and installing hamachi for ubuntu.. I can't recommend Hamachi ... it hasn't been updated in ages (last release is from 2007?) and I am not even sure it will work with present-day kernels.

If you want to try out a similar product, why not try Remobo? They've released their software in a proper Ubuntu version too, so it should be way easier and less painful.

[http://www.remobo.com/download.php](http://www.remobo.com/download.php)

---

### Post by sandyd on 2009-08-22
[http://www.google.ca/url?q=http://www.supware.net/HamachiUbuntuHowto/&ei=2mmQSsm7NYK0lAeGiNWjDA&sa=X&oi=spellmeleon_result&resnum=1&ct=result&usg=AFQjCNHdMtSWVyTZ7-Oog9--et_0dto5UA](http://www.google.ca/url?q=http://www.supware.net/HamachiUbuntuHowto/&ei=2mmQSsm7NYK0lAeGiNWjDA&sa=X&oi=spellmeleon_result&resnum=1&ct=result&usg=AFQjCNHdMtSWVyTZ7-Oog9--et_0dto5UA)

---

### Post by scorp123 on 2009-08-22
> **carlee said:**
> [http://www.google.ca/url?q=http://www.supware.net/HamachiUbuntuHowto/&ei=2mmQSsm7NYK0lAeGiNWjDA&sa=X&oi=spellmeleon_result&resnum=1&ct=result&usg=AFQjCNHdMtSWVyTZ7-Oog9--et_0dto5UA](http://www.google.ca/url?q=http://www.supware.net/HamachiUbuntuHowto/&ei=2mmQSsm7NYK0lAeGiNWjDA&sa=X&oi=spellmeleon_result&resnum=1&ct=result&usg=AFQjCNHdMtSWVyTZ7-Oog9--et_0dto5UA) OK, so it does work, despite not having been updated since 2007 .... Thanks for posting that guide.

---

### Post by sandyd on 2009-08-22
wait. this guide is so freaking old that
```

tar -zxvf hamachi-0.9.9.9-x.tar.gz
cd hamachi-0.9.9.9-x/

```
should be
```

tar -zxvf hamachi-*tar.gz
cd hamachi-*/

```

p.s.
that only installs hamachi, with NO gui.
recommended:  [http://quamachi.sourceforge.net/](http://quamachi.sourceforge.net/)
use the deb.

---

### Post by sandyd on 2009-08-22
p.s. don't use the hamachi deb from
[http://code.google.com/p/quamachi/downloads/list](http://code.google.com/p/quamachi/downloads/list)
even though its there. it has some problems. (or at least it had some problems on mine)

---

### Post by howefield on 2009-08-22
> **scorp123 said:**
> If you want to try out a similar product, why not try Remobo?

Maybe because it is in Beta testing ?

---

### Post by scorp123 on 2009-08-22
> **howefield said:**
> Maybe because it is in Beta testing ? And so? You know that Ubuntu is based on Debian's "testing" tree, right? 

[http://www.ubuntu.com/community/ubuntustory/Debian](http://www.ubuntu.com/community/ubuntustory/Debian)

So given that your entire OS is another OS's "beta code" I guess you shouldn't be too worried about one single package in "beta" status?

---

### Post by howefield on 2009-08-22
> **scorp123 said:**
> And so? You know that Ubuntu is based on Debian's "testing" tree, right? 

[http://www.ubuntu.com/community/ubuntustory/Debian](http://www.ubuntu.com/community/ubuntustory/Debian)

So given that your entire OS is another OS's "beta code" I guess you shouldn't be too worried about one single package in "beta" status?

Calm down, did I touch a nerve ?

You asked the question "why not try Remobo?"

I gave you one reason that might make someone uncomfortable (actually, there are several more that would make people wary of using this program). 

Do you disagree some people might find that a legitimate reason ?

Incidentally, you shouldn't presume what "my" operating system is or what I should  worry about. :lolflag:

---

### Post by scorp123 on 2009-08-23
> **howefield said:**
> Calm down ...  No need, I am not upset or anything like that :D    .... Never mind. Misunderstandings happen. :)

> **howefield said:**
>  Do you disagree some people might find that a legitimate reason ? No ... but if someone (and I mean that in a general sense here, not you personally) is so worried about "stability" ("stability" is a relative term anyway IMHO and absolute stability doesn't exist IMHO) and these things that you listed, I'd then rather expect such a user to use Debian "stable", RHEL, CentOS or a similar OS ... I'd not expect to encounter this type of user here in the Ubuntu forum too often. 

On Linux tinkering with stuff that's in "beta" status is almost a "must", it more or less comes automatically with being a Linux user, and one shouldn't be too afraid of that, IMHO. (unless it's an experimental kernel patch or something which could render your system unusable ... )

So ... if someone is hanging around here in the Ubuntu forum, I'd either expect such a user to soon to switch or to already be using Ubuntu.

... So, by that logic, if someone is OK with running Ubuntu --which basically is a snapshot of Debian "testing"-- then I'd also assume that one single non-OS-essential package (= whether or not it really works or not won't have any consequence for the rest of your OS) in "beta" status won't hurt too much either ...

I hope this explains my thoughts and why I brought up the argument about Ubuntu being "beta" anyway? :)

BTW, lots of packages in Linux have version numbers like 0.xx (zero dot something). Hamachi too in its Linux variation is at version 0.99 since at least 2006/2007 so I'd assume it isn't far away from a "beta" either, given that the Windows and Mac version numbers are way higher (and the clients there are much further advanced then the Linux version). And the fact that development of Hamachi has been at a standstill since at least 2007 (when LogMeIn took over Hamachi) tells me that there have not been any updates, patches, code review and what not since at least 2 years.

So even if "Remobo" is a "beta" right now: at least it's in active development and by beta-testing it now, one could still influence the program's design e.g. by giving feedback to the developpers. Also: if they get feedback from a lot of Linux users then this might motivate them (and others?) to keep producing a Linux version. Hamachi's Linux version is more or less dead since two years and the developers don't really give one smelly kilobyte about what Linux users think. I have had my share of clashes with the main developer there and my opinion about Hamachi as a company (now part of LogMeIn Inc.) is rather low.

So yes, I am slightly biased too. :D

---

### Post by howefield on 2009-08-23
> **scorp123 said:**
> No need, I am not upset or anything like that :D    .... Never mind. Misunderstandings happen. :)

That's good. :)

>  No ... but if someone (and I mean that in a general sense here, not you personally) is so worried about "stability" ("stability" is a relative term anyway IMHO and absolute stability doesn't exist IMHO) and these things that you listed, I'd then rather expect such a user to use Debian "stable", RHEL, CentOS or a similar OS ... I'd not expect to encounter this type of user here in the Ubuntu forum too often.

You see, that is a pretty presumptious statement to make about the people who come to ubuntuforums, there is a huge diversity of posters here who come for many differing reasons and who have many differing levels of skill and knowledge. You make it sound like using Ubuntu is some sort of bravado risk taking experience.

> On Linux tinkering with stuff that's in "beta" status is almost a "must", it more or less comes automatically with being a Linux user, and one shouldn't be too afraid of that, IMHO. (unless it's an experimental kernel patch or something which could render your system unusable ... )

And the acceptable level of risk one is prepared to take is down to the user to determine, not someone else. 

> So ... if someone is hanging around here in the Ubuntu forum, I'd either expect such a user to soon to switch or to already be using Ubuntu.

There you go again, being all presumptious ;) and to be honest, irrelevant as to whether or not you should be a bit more upfront when promoting unsupported (as in outside the normal install/repository) software.

> ... So, by that logic, if someone is OK with running Ubuntu --which basically is a snapshot of Debian "testing"-- then I'd also assume that one single non-OS-essential package (= whether or not it really works or not won't have any consequence for the rest of your OS) in "beta" status won't hurt too much either ...

I hope this explains my thoughts and why I brought up the argument about Ubuntu being "beta" anyway? :)

More assumptions, at least you recognise it this time, I'd counter that Ubuntu is a little bit more than a snapshot of Debian testing, you are being a little disingenuous, but that is neither here nor there, the point is that posters here are required under the code of conduct to explain any risks when asking users to use software outside "normal" channels. Running Beta software is a risk, however low or high it may be, I'd hope that you would concede that you should be upfront about that (and your other "biases" which you outline later). 

Your almost casual/throwaway line explains absolutely none of the risks, 
"If you want to try out a similar product, why not try Remobo? They've released their software in a proper Ubuntu version too, so it should be way easier and less painful." but spins it in a way that it looks better than it is.


> BTW, lots of packages in Linux have version numbers like 0.xx (zero dot something). Hamachi too in its Linux variation is at version 0.99 since at least 2006/2007 so I'd assume it isn't far away from a "beta" either, given that the Windows and Mac version numbers are way higher (and the clients there are much further advanced then the Linux version). And the fact that development of Hamachi has been at a standstill since at least 2007 (when LogMeIn took over Hamachi) tells me that there have not been any updates, patches, code review and what not since at least 2 years.

Err... thanks for the lesson. What's Logmein/Hamachi got to do with explaining the risks of running Remobo in Beta stage ?

> So even if "Remobo" is a "beta" right now: at least it's in active development and by beta-testing it now, one could still influence the program's design e.g. by giving feedback to the developpers. Also: if they get feedback from a lot of Linux users then this might motivate them (and others?) to keep producing a Linux version. Hamachi's Linux version is more or less dead since two years and the developers don't really give one smelly kilobyte about what Linux users think. I have had my share of clashes with the main developer there and my opinion about Hamachi as a company (now part of LogMeIn Inc.) is rather low.o. :D

So yes, I am slightly biased too. 

Some of this in your original post might have been of benefit.

---

### Post by mapes12 on 2009-08-23
> **scorp123 said:**
> I can't recommend Hamachi ... it hasn't been updated in ages (last release is from 2007?) and I am not even sure it will work with present-day kernels.

If you want to try out a similar product, why not try Remobo? They've released their software in a proper Ubuntu version too, so it should be way easier and less painful.

[http://www.remobo.com/download.php](http://www.remobo.com/download.php)Hi scorp123

Last time we looked at Remobo we identified the DECnet issue. See here: [http://ubuntuforums.org/showpost.php?p=7763198&postcount=21](http://ubuntuforums.org/showpost.php?p=7763198&postcount=21)

Do you know if the developers have sorted this out yet? I have found the easiest solution to be [http://www.yuuguu.com/download/linux_download_preview](http://www.yuuguu.com/download/linux_download_preview)

I know that they also have a commercial app but the free version is very easy to use.

---

### Post by scorp123 on 2009-08-23
> **mapes12 said:**
> Last time we looked at Remobo we identified the DECnet issue. See here: [http://ubuntuforums.org/showpost.php?p=7763198&postcount=21](http://ubuntuforums.org/showpost.php?p=7763198&postcount=21) Oh blasted!! I completely forgot that thread ... :(  Now that you've said the magic word "DECnet" I all of a sudden remember myself _NOT_ recommending Remobo ... LOL. I guess I'm in need of vacation or something ... 

OK, with that DECnet dirt (it changes one's MAC addresses!!) still being a dependency I take back what I wrote ... [B][COLOR="Red"]Remobo's *.deb package is broken and shouldn't be used!
[/COLOR][/B]

[http://ubuntuforums.org/showpost.php?p=7763198&postcount=21](http://ubuntuforums.org/showpost.php?p=7763198&postcount=21)
[http://www.remobo.com/community/viewtopic.php?f=4&t=278](http://www.remobo.com/community/viewtopic.php?f=4&t=278)

> **howefield said:**
>  Some of this in your original post might have been of benefit.   It might have been of benefit if I had used my brain .... That's what I get for using Google a slight bit too much.

You're right. You win. Remobo --at least the current build-- is BS. For totally stupid reasons it has various DECnet components as dependency even though it's not even using DECnet at all. But DECnet relies on changing the MAC addresses of all interfaces ... so this will seriously interfere with anything else network-related (especially DHCP). Bad idea.

 And if I had taken care to remember the name "Remobo" instead of googling about "zero conf VPN" again, I might also have remembered myself _NOT_ recommending Remobo. Taddaaa. :lolflag:

Oh well. You were right. I was wrong. :D

---

### Post by howefield on 2009-08-23
> **scorp123 said:**
> Oh blasted!! I completely forgot that thread ... :(  Now that you've said the magic word "DECnet" I all of a sudden remember myself _NOT_ recommending Remobo ... LOL. I guess I'm in need of vacation or something ...

Approved, somewhere nice I trust ?  ;)

---

