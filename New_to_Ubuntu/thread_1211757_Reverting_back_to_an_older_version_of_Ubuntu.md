---
title: "Reverting back to an older version of Ubuntu"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Wisey on 2009-07-13
Hello, I installed Ubuntu Jaunty a while back, but I have been having problems with graphics with my Intel Chipset. Earlier I couldn't even get Compiz to start, but after reverting back to an older driver, I now have visual effects, but the screen becomes really choppy when those effects actually come into use. 

I am kind of tired of searching around for solutions, I don't want to switch back to windows again, so I thought of reverting to an older version. I thought of Hardy, since the chaos of my first two weeks of Jaunty has somewhat led me to prize stability a bit more, and maybe Intrepid. LTS sounds attractive to me now, but I am kind of apprehensive of being stuck with out of date applications, how much more advanced are Intrepid and Jaunty when compared to Hardy? Won't the updates to Hardy somewhat level it up with the other two?

Also, I have no idea about how to revert back to the older versions, do I just download the image file and install all over again? Won't that lead me to lose all my data? I can't backup my files to DVDs or anything, this silly computer that I borrowed doesn't even have a writer. 
Keeping all that in mind, can someone please tell me what to do? Oh yea, I also have Windows XP installed on this machine, it is not mine, so I can't go around removing it.
Edit - Oh yea, I have also been thinking about Kubuntu, I didn't have any idea about it earlier so I just went with the normal Jaunty installation, can someone please tell me the advantages and disadvantages of Kubuntu?

---

### Post by rockerphil on 2009-07-13
if you're wanting to revert back to an older version of Ubuntu my best advice is to move your personal data to the XP install so that you don't wipe out your files, then i'd personally download Hardy and install that. as far as out-dated apps goes Hardy is still supported and updated so you'll get the same application updates that Jaunty and Intrepid do. hope this info helps,

Phil
edit: the only difference between Ubuntu and Kubuntu is that Ubuntu runs Gnome and Kubuntu runs KDE, so the only difference is the interface, it's still the same system under the hood, just diferent applications (I.E. Konquerer fo the file browser instead of Nautilus)

---

### Post by Wisey on 2009-07-13
Thank you! A rather simply(and obvious) solution to the data problem that just didn't hit me.
However, I don't get this, if Hardy is as up to date as Intrepid and Jaunty, why do people even bother installing the short term releases? I mean what benefit do they acquire by installing a newer version when they would be getting the same updates on Hardy itself?

And are there any performance differences between Kubuntu and Ubuntu? Extra apps maybe? Some incompatibilities? Anything? If they are basically the same thing, then why do some people prefer one and not the other?

---

### Post by nhasian on 2009-07-13
the intel graphics driver was blacklisted because it caused lockups.  the issue is fixed now with Karmic, so if you wanted to upgrade instead of downgrade that would resolve your issue too :)

---

### Post by Irihapeti on 2009-07-13
Hardy gets security updates, and the updates to Firefox 3.0.x, but all the other programs are older than in later versions of Ubuntu and don't get updated when a new version of the program comes out.

There are some ways around this, such as enabling PPA repositories for particular programs, getting .deb files from sites such as Getdeb or the programmers website, and compiling from source. Obviously, the last option won't suit a lot of people, and some don't feel comfortable with the idea of getting programs from places outside of the official repositories.

That might help explain things a bit. In the end, it's up to you to decide.

---

### Post by Wisey on 2009-07-13
@nhasian
I think I will wait for Karmic to come out stable, and then try it out for a while with a live CD to make sure everything is working. I am a bit sour from my experience with Jaunty.

@Irihapeti
Well that explains things a little I guess, thank you.

I don't mind using old versions of programs as long as they work. If I am not happy with it, I can just upgrade to the Koala in October.

I guess its going to be Hardy for now then, thank you for the replies!

---

### Post by muteXe on 2009-07-13
> **nhasian said:**
> the intel graphics driver was blacklisted because it caused lockups.  the issue is fixed now with Karmic, so if you wanted to upgrade instead of downgrade that would resolve your issue too :)

And probably cause a load more problems associated with new releases.

---

### Post by Bradtek on 2009-07-13
Did you try this

HOWTO: Jaunty Intel Graphics Performance Guide 
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

It helped with a minor problem I was having with Video Playback

---

### Post by t0p on 2009-07-13
> **Wisey said:**
> 
I guess its going to be Hardy for now then, thank you for the replies!

I can definitely recommend Hardy.  I've had it on my desktop machine for a year or so now, and I intend to stick with it for a good while yet.

In the past I installed a new release every 6 months - I still do that on my EeePC.  But it was getting to be a real pain on my desktop machine, which is the box I do most of my serious work on.  So I decided: LTS for me!  And it's worked out great.  There's a couple of apps on it that I've upgraded manually (Firefox, and I think vlc) but other than that I'm happy with the software versions on it.  Maybe they're not all the lastest and greatest, but they do the job and it's not like they're awfully out-dated or anything - maybe 12 months old, and still fully-supported.

New releases are fantastic for testing or fun.  But when it comes to work, stability is a great asset.  Long live Hardy Heron!

---

### Post by carml on 2009-07-13
> **t0p said:**
> I can definitely recommend Hardy.  I've had it on my desktop machine for a year or so now, and I intend to stick with it for a good while yet.

In the past I installed a new release every 6 months - I still do that on my EeePC.  But it was getting to be a real pain on my desktop machine, which is the box I do most of my serious work on.  So I decided: LTS for me!  And it's worked out great.  There's a couple of apps on it that I've upgraded manually (Firefox, and I think vlc) but other than that I'm happy with the software versions on it.  Maybe they're not all the lastest and greatest, but they do the job and it's not like they're awfully out-dated or anything - maybe 12 months old, and still fully-supported.

New releases are fantastic for testing or fun.  But when it comes to work, stability is a great asset.  Long live Hardy Heron!

+1

Take in mind that upgrading only application can also give you some pain when the upgrade envolves any common dependences,for example there's some issue between the version of Python in Hardy and the latest version because of the imporovement realized in the components of Python. :)

---

### Post by Wisey on 2009-07-13
> **Bradtek said:**
> Did you try this

HOWTO: Jaunty Intel Graphics Performance Guide 
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

It helped with a minor problem I was having with Video Playback
Yep. Didn't notice any difference. 

Thing is, I think I might need that stability even without the video problem, since the computer isn't mine, I don't think I can take the risk of messing up while trying to fix something. I already reinstalled once, then I did something which resulted in a grey screen in which I couldn't do anything, I couldn't even open the terminals with Ctrl+Alt+F2. Afterwards I somehow got compiz to work, don't even know what I did to be truthful, but now I have the choppy screen with even a bit of visual effects enabled.

Hardy Heron it is for me. :) I will install the latest releases on my laptop, which I will probably buy in the near future anyway.

---

### Post by nhasian on 2009-07-13
in jaunty, because your intel video driver was blacklisted, did you try re-enabling it?

[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

btw, i've been using Ubuntu 64 bit Karmic Alpha2 since it came out with no problems.

---

### Post by TeamJ on 2009-07-13
the intel drivers ar crap but will be fixed in karmic.until then try UNR, it is built for netbooks with intel graphics and works around that

---

