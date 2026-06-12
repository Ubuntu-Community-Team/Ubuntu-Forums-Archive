---
title: "I'm looking into switching from windows..."
date: 2009-06-22
forum: New to Ubuntu
---

### Post by MordeaniisChaos on 2009-06-22
But before I make the decision, I need to make sure I can still do all the things I need to do, and a few things I've been meaning to do.
 
First of all, Instant Messengers. I really only need to be able to communicate with MSN, and I am probably going to use aMSN, but what about AIM?
 
Also, I'd like some software I could use to create and manage a podcast. It needs to be able to record and that's about it, but I would really love something with decent editing, and a good GUI. Nothing to complicated, as I'm new in the podcast arena =)
 
Also, Media players-Are the defaults decent enough? I just need to be able to watch wmvs from the likes of Gamersyde.com.
 
And as for flash video, am I good on that?
 
I know its a lot of questions, and I probably have a million more, but this will help me alot in figuring out if I want to switch or not (which I'm already pretty sure I do ^.^)

---

### Post by sideffects on 2009-06-22
For instant messenger Pidgin is my favorite. (Comes pre-installed.) Does all the main messenger services. Google/MSN/ICQ/AIM/Yahoo/Facebook/Myspace and more.
I haven't messed around with podacasts in Ubuntu, but I'm sure there is software.
I don't like the media players in Ubuntu as much as I like iTunes, but they will do what you need. You should use Amarok which only comes pre-installed in Kubuntu, but you can download it in Ubuntu.
Flash in Firefox works just fine.

---

### Post by jonobr on 2009-06-22
Hello

And welcome to the forums, where we specialize in trying to ween users away from windoze.... :-)

If you look around you will find a lot of links comparing applications on ubuntu to apps on linux,
theres a tonne of resources.

One thing you could do if your not sure about making a switch, is to use wubi, which is built for people like your good self to assess ubuntu before making the switch.

In Wubi, ubuntu is installed like an application on windows, so you dont loose any windows stuff or data.

[HERE]("http://en.wikipedia.org/wiki/Wubi_(installer)") a wiki on Wubi

and [Here ]("http://wubi.sourceforge.net/") is the wubi homepage where you can download the code.

For the questions you ask,

Yep theres apps available for those,
specifically for msn, you mentioned you can use amsn, however, pidgin is a much better option which integrates all you im needs

The media players are ok, you can use a program like amorak 
For the flash question, yep it will work, however, some people have ahd problems with it, but people here are willing to help if you do run into issues,


When you install you ubuntu version you want,.
you should go to system-> adminsitration and synaptic.
heres where you install you software from.

In there you can type simple searches to find the software you want.

Lastly, if you have the time, I would read the ubuntu pocket book just to get you started. It will ease you integration with Ubuntu

Cheers and GOOD LUCK

---

### Post by Tyke91 on 2009-06-22
```
First of all, Instant Messengers. I really only need to be able to communicate with MSN, and I am probably going to use aMSN, but what about AIM?
```Use pidgin. It is pre-installed with Ubuntu and is very slick. 
 
```
Also, I'd like some software I could use to create and manage a podcast. It needs to be able to record and that's about it, but I would really love something with decent editing, and a good GUI. Nothing to complicated, as I'm new in the podcast arena =) 
```Audacity can record sound for you. I don't know if it is podcast worthy because I've never made a podcast before :) but the GUI is easy enough to use and it's got some pretty nice sound manipulation features (I've used it to create song mixes and such)

```
Also, Media players-Are the defaults decent enough? I just need to be able to watch wmvs from the likes of Gamersyde.com.
```The built in media players are enough, but I would recommend VLC just for its versatility. You can find VLC in the repositories (which you will grow to love :) )
 
```
And as for flash video, am I good on that?
```Yes :) Easiest way to install flash is to just go to youtube and click the download link when it prompts you to.
 
```
I know its a lot of questions, and I probably have a million more, but this will help me alot in figuring out if I want to switch or not (which I'm already pretty sure I do ^.^)
```Don't be afraid to ask, and welcome to the community! :)


PS: Amarok is very shiny, but I like Exaile better (it's faster and can use a ton of plugins) Either are nice.

---

### Post by ainsworth_t on 2009-06-22
> First of all, Instant Messengers. I really only need to be able to communicate with MSN, and I am probably going to use aMSN, but what about AIM?
Pidgin is a multi-protocol instant messaging client that you can use for both your MSN and AIM accounts and it is installed by default (though will be replaced by Empathy in the 9.10 release I believe, but it will have the same functionality). You can check the project web site or Wikipedia page for a list of all the supported protocols. Pidgin has a Windows version that you can install and try out first if you'd like.

> And as for flash video, am I good on that?
Yeah, all you'll have to do is install ubuntu-restricted-extras and it will install flash player for you. You can either install it from the Synaptic Package Manager (System >> Administration >> Synaptic Package Manager) or from the command line:

```
sudo apt-get install ubuntu-restricted-extras
```

> Also, Media players-Are the defaults decent enough? I just need to be able to watch wmvs from the likes of Gamersyde.com.
The default media players should be enough after you install the ubuntu-restricted-extras package, but if you want, you can install VLC, it supports a ton of video formats (once again, you can check out the project site for a list of supported formats). VLC also has a Windows version that you can try before you switch. Within Ubuntu, you can install VLC either from Synaptic or from the command line:

```
sudo apt-get install vlc
```

As for creating and editing Podcasts, I've never done it, so I'm not sure in what direction to point you.

If you are still uncomfortable with switching, first you can try Ubuntu out with the Live CD (Select the "Try Ubuntu Without Installing" option after booting into the CD). Then if you like it but are still uncertain about switch, try installing it within a Virtual Machine (I suggest using VirtualBox which can be found [here]("http://www.virtualbox.org")). If you are still uncomfortable with a full switch after that, try a dual-boot environment. I would suggest using the [Wubi ]("http://wubi-installer.org")installer for your dual-boot environment because it's beginner-friendly and it doesn't do a true dual-boot and mess with your hard drive. It basically installs Ubuntu as a program within Windows that can then be booted into at startup. If you don't like it, you can remove it from Add/Remove Programs.

Hope this helps!

---

### Post by sideffects on 2009-06-22
Yes, I would also recommend VLC, unless you want all of your media in a library in which case use Amarok or Songbird.

---

### Post by Temposs on 2009-06-22
Pidgin is good for instant messaging, any service you use, pidgin likely supports it. It comes with Ubuntu

For audio recording and editing, try Audacity. There's a Windows and Mac version, too, so you can try it out on Windows to see if you like it. It wins awards.

There are many video players for Ubuntu and they will play most anything(once you have installed the codecs, which is mostly done automatically when you open a new file). Try VLC for a video player. It bundles a lot of its own codecs, so you don't need to worry about getting them. There's a Windows version of that, too. It will play anything, and better than most other players, on Windows or Linux.

For music, the default Rhythmbox that comes with Ubuntu I find to be quite good, and I can play and organize all my music through that.

---

### Post by aufan19 on 2009-06-22
Pidgin supports AIM and MSN. It's included with Ubuntu by default.

Audacity is supposed to be pretty good for audio editing/recording. It's in the repositories.

There is a media player called VLC that is excellent. I think it can play WMVs. You can install that through the repositories.

For me, Flash is fine on linux. I've only experienced one problem (slow video right after I installed it), and a restart fixed it. Ubuntu does not ship with certain fonts, flash, or certain multimedia codecs, but one terminal command can install all of that for you. Just open the terminal and type:

"sudo apt-get install ubuntu-restricted-extras" (no quotes)

Press 'y' to confirm the installation, and it will install fonts, codecs, and flash.

---

### Post by medic2000 on 2009-06-22
Emesene also a good client for MSN. Dont forget to activate its plugins for much more comfortable experience.

For movies i highly recommend SMplayer. And for music Rhythmbox is very good.

This is important: After installing Ubuntu go and install "ubuntu-restricted-extras" from repos. 

Then add the medibuntu repos and install "w32codecs" and "libdvdc2" for dvd,wma,wmv etc.. support. 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If you have a problem ask the forums,google it and you will seek out the solution quickly.

---

### Post by shifty_powers on 2009-06-22
I haven't had to do that with the medibuntu repo's for aaaaaages....

---

