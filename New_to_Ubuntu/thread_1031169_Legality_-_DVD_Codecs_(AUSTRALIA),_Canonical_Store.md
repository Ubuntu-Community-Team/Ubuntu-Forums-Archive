---
title: "Legality - DVD Codecs (AUSTRALIA), Canonical Store Products"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Ji Ruo on 2009-01-05
I bought my computer second hand from a local community group, with Kubuntu as the installed OS and VLC as the DVD playback software. Recently I've done a completely new install of Ubuntu 8.10, so that I could set up mobile broadband, and it's worked out very well for me so far.

However I am finding it difficult to determine the exact legal status of downloading the restricted DVD (and mp3) Codecs in Australia. Am I right in assuming, because of the lack of information, that this is somewhat of a grey area ?

In the case of any ambiguity about this I will probably end up downloading one of the products from the Canonical store for ethical reasons. I am baulking at the price - $49.95US for Power DVD, for which I could easily get a DVD player for a TV - but I don't have much else in terms of workable solutions: 

- I don't want to buy a DVD player because of space limitations (I gave away my TV recently for this reason), and it's wasteful when I already have the hardware right in front of me. 
- Ripping the DVDs to another format seems to be out, because they're mostly borrowed or rented. I could consider just deleting the files after use, but I'm not sure if this presents a legal issue ?
- I could buy a copy of XP and partition the hard drive, for the express purpose of watching restricted formats. Again not the most elegant or desirable solution.
- The Fluendo products that are also listed at the Canonical store are cheaper, but don't expressly list DVD playback, so can I assume that it's not supported ?

You might be able to see why the restricted formats issue is gradually coming to look like the elephant in the room for me! If anyone can confirm the legal status of the Codecs, or supply any further information or solutions I'd really appreciate it.

- Edward

---

### Post by 3rdalbum on 2009-01-05
To my knowledge, the "free" DVD playback is not legal in Australia; but be aware that I am just relaying something that I have heard from some guy on the Internet.

I strongly believe that the patented codecs are illegal in Australia too, except for the free Fluendo MP3 playback codec which is fully licensed.

---

### Post by Ji Ruo on 2009-01-05
> **3rdalbum said:**
> To my knowledge, the "free" DVD playback is not legal in Australia; but be aware that I am just relaying something that I have heard from some guy on the Internet.

This is about as strong evidence as I could find on this from my own searching... I'm sure you can see why I'm after some clarification on this.

Thanks for your help.

---

### Post by aimwin on 2009-06-25
Dear the GURUs

1st issue.

Can someone from Canonical legal department? or some lawyers in the forum could help telling us more about where can we check for legal use of the codec in each country?

Can we buy those licenses and are they expensive?


2nd issue.
What are the differences that Cononical provide the automatic download click and the instruction how to download and install?

I presume there are, since providing information is not illegal, but installing into the computer is illegal.

Then can we make all of the links in page 
[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)
and the
sudo /usr/share/doc/libdvdread3/install-css.sh
into one link.

So, the new ubuntu user who don't know much about command line or know nothing about the command line terminal can just click once and that is it.

Or that information page is on the installation pop up screen with warning and a tick box said I have check and it is legal for me to use the restricted format.

If the user click yes I want to install, then the installation will include all the codecs and what ever.... from the installation CD and everything is ready for user, including VLC.

---

### Post by Ji Ruo on 2009-06-26
I'm definitely not one of the gurus, but I'll contribute what I've learned since I posted this thread a few months ago.

You can assume that it is not available legally for free. This is because the codec is owned by one or more companies and they charge for its use or restrict it in some other way. In the case of the DVD codec, I have read somewhere that it's many, many companies who own the codec and they all receive a small portion of the royalties for its sale each time someone purchases the software/hardware that allows you to play dvds.

The dvd codec which is available has been reverse engineered by someone in the past, and released for free on the net. There would be some countries where this is not illegal, however they are sure to be the exception rather than the rule. If your decision on which codec to use is based on ethics as well as legality, then this might already mean that you don't want to use the hacked codec when there is a legal alternative available.

Now, the dvd codec is actually the MPEG2 codec, so there is a copy included in one of the fluendo products available. That means you have two legal choices available for purchase from the canonical store - fluendo (the one that includes MPEG2), and the cyberDVD package.

I ended up buying a copy of Vista for $300AUD, which I thought would solve some issues I was having with this and some other things (a website I wanted access to that used direct X, anticipated issues with my uni website etc). But no, I'd bought the Home Basic edition (the cheapest) and the DVD codec was not included! I had to download it for a fee from a reseller (an extra $20AUD). Apparently this was also the case with Widnows XP Home edition - no dvd codec included. So ubuntu is far from alone in having these issues! I think the best way to get the codec would be to buy the fluendo package, as you get just about every other codec you'll ever want as well. With the cyberdvd package you're largely paying for the software, and if you're happy with vlc media player it might be unnecessary expenditure.

---

### Post by t0p on 2009-06-26
> **aimwin said:**
> Dear the GURUs

1st issue.

Can someone from Canonical legal department? or some lawyers in the forum could help telling us more about where can we check for legal use of the codec in each country?


Can I suggest that you send your questions to Canonical?  While the whois info lists Canonical Ltd as the registrant, this site is actually an unofficial forum that Canonical very kindly host on their servers.  You might get lucky and have a Canonical lawyer browse the forum during her lunch break, but if that happens it is very unlikely she will reply to you in a professional capacity.

As for the general point of asking for legal advice in an online forum: the best you're likely to get is very inexact comments prefixed with IANAL (I Am Not A Lawyer).  If you want definitive advice about the law where you live, go see a lawyer.  You pay 'em, they'll tell you anything!

---

### Post by mikechant on 2009-06-26
There appears to be some confusion going on. There are two issues here: The mpeg codecs and the content scrambling system for DVDs.
Generally speaking, the mpeg codecs are distributed with most distros in all countries, and although they may be patents involved, I'm pretty sure that the patent holders have stated they will not enforce them against this sort of use - otherwise Canonical etc. would not be distributing them in this unrestricted way. The mpeg codecs will enable you to play standalone mpeg files and unencrpyted DVDs with mpeg files on.

However, most commercially pressed DVDs are encrpyted with CSS - content scrambling system. The legal issue with this is not patents or copyrights etc. but the US DMCA (digital millenium copyright act) or local equivalent.
My understanding of the US version is that it makes it illegal to *distribute* the deCSS software which decrpyts the DVD but not to *posess* it. If your local law is the same then it is not illegal for you to obtain deCSS, and if the server distributing it is in a country with no DMCA equivalent then there should be no legal issues and you can use it with a clear conscience.
deCSS was ruled to be legal in the country it was created (Norway I believe) - google 'DVD Jon deCSS' for more info.

Anyhow, I'm not a lawyer and this is not legal advice! This is just the general impression I've picked up from reading about this topic over the last few years.

Ethically, personally I believe that as I have bought a legal DVD I have the moral right to play it in any way I choose with any software I choose on any OS I want to if I can get it to work.

---

### Post by t0p on 2009-06-26
> **mikechant said:**
> 
Ethically, personally I believe that as I have bought a legal DVD I have the moral right to play it in any way I choose with any software I choose on any OS I want to if I can get it to work.

That is how I would justify to myself my use of libdvdcss.  If I ever felt the need to justify it to myself.

Fortunately, I'm one of those "unethical" "pirates".  And as such, I rarely find my conscience troubled by these matters.

Needless to say, I am in no way condoning the breach of intellectual property laws.  Don't drink and drive, kids!

;)

---

### Post by stinger30au on 2009-06-26
the best way i play my dvds using ubuntu for zero bux is to go to applications and click add remove and hit how all and search on restricted extra and put a tick in the box

next i visit medibuntu and follow their instructions for what ever virsion i have

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

been doing this since 7.04 and im yet to be told differently by a lawyer/solictor/police officer/ judge/prime minister/ minster for communications/premier of queensland/ the pope /the queen/ god/ satan/the voices in my head/or anyone/or anything else of significance

---

### Post by Hallvor on 2009-06-26
Who cares? There is nothing to worry about unless you distribute it, and perhaps not even then. It`s not like some SWAT team will knock down your door in the middle of the night and drag you out in handcuffs because you download it.

Playing DVDs that you have bought on your DVD player is fair use, imho.

But then, I am not a lawyer, and in this case, I don`t care much what they say. I use common sense.

---

### Post by k3lt01 on 2009-06-26
> **mikechant said:**
> Generally speaking, the mpeg codecs are distributed with most distros in all countries, and although they may be patents involved, I'm pretty sure that the patent holders have stated they will not enforce them against this sort of use - otherwise Canonical etc. would not be distributing them in this unrestricted way. The mpeg codecs will enable you to play standalone mpeg files and unencrpyted DVDs with mpeg files on. Aren't the Codecs part of MediBuntu? Restricted Extras package from memory. In which case Canonical is NOT the originating distributor. Furthermore MediBuntu was created for the purpose of distributing such things because of restrictions such as copyright etc that a company such as Canonical doesn't want to have to deal with.

To the OP, and anyone else concerned about this type of thing, I hate to say it but this is certainly not the place to be asking this question as you certainly wont receive any definitive legal advice that will stand up in a court in this country. I'll go even further and say that no Common Law jurisdiction (ex English colony) will take what is stated on ubuntuforums.org as a defense if you are in the unfortunate position of getting caught out. In Common Law ignorance is NOT a defensible position, you the individual are supposed to know before you use your equipment, possessions, playthings, toys, etc, what you can and cannot legally do with it.

---

### Post by Mornedhel on 2009-06-26
> **k3lt01 said:**
> Aren't the Codecs part of MediBuntu?

I can at least get libmpeg2-4 from the universe repositories. As others pointed out, MPEG is not free but the organization that maintains them has stated it will not sue anyone for distribution. libdvdcss2 is the problem, since it's illegal to distribute it in most notably the USA, and thus it's in the Medibuntu repositories.

---

### Post by k3lt01 on 2009-06-26
> **Mornedhel said:**
> I can at least get libmpeg2-4 from the universe repositories. As others pointed out, MPEG is not free but the organization that maintains them has stated it will not sue anyone for distribution. libdvdcss2 is the problem, since it's illegal to distribute it in most notably the USA, and thus it's in the Medibuntu repositories.Well this thread is about Australia but in Legalese a precedent has been set in a Common Law country (notably the USA) and that precedent can be used in other Common Law jurisdictions. However that is all beside the point at this moment in time because we are not talking about legal precedents.

[help.ubuntu.com]("https://help.ubuntu.com/community/Repositories/Ubuntu") says:

The repository components are:
    * Main - Officially supported software.
    * Restricted - Supported software that is not available under a completely free license.
    * Universe - Community maintained software, i.e. not officially supported software.
    * Multiverse - Software that is not free. 

The Restricted Extras package is actually in the Multiverse Repo which from above means it is NOT free. Adding to this, it "pulls" software from the Universe Repo which Canonical does NOT officially support.

MediBuntu has 3 sections, or Repos for the want of a better term, Free, Multiverse and Non-Free. libdvdcss2 is in the Free section so it should not be a problem.

Like I said the issue isn't going to be answered adequately here because it is up to individuals to know what is legal in their country.

---

### Post by SunnyRabbiera on 2009-06-26
Personally I say screw it, install libdvdcss and to heck with legality.
The current system only benefits the greedy and the corrupt, so why not even the playing field.

---

