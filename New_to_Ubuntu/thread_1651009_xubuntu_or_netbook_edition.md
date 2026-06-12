---
title: "xubuntu or netbook edition?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by semetay on 2010-12-22
hello,

I cant decide which one to install so any help is appreciated. I have a little desktop (barebone rather) with a foxconn motherboard and atom single core. I currently have winxp installed and I use this mainly for watching youtube and some other web streaming sites. one of the sites uses silverlight and quality of the video changes dynamically depending on the internet connection and the hardware. since I have a single core atom cpu on this machine, so the the quality is terrible. I can stream in HD on my laptop on the same wireless network so internet connection speed is not the issue here.

So I figured maybe I could get a better quality if I install an OS which uses very little resources. I am down to two choices, ubuntu netbook edition or xubuntu. I am leaning towards the netbook edition since it is optimized for atom cpus and also it uses a USB drive for installation (I dont have optical drive on this machine).

thank you in advance for all your feedback...

cs

---

### Post by erilidon on 2010-12-22
> **semetay said:**
> hello,

I cant decide which one to install so any help is appreciated. I have a little desktop (barebone rather) with a foxconn motherboard and atom single core. I currently have winxp installed and I use this mainly for watching youtube and some other web streaming sites. one of the sites uses silverlight and quality of the video changes dynamically depending on the internet connection and the hardware. since I have a single core atom cpu on this machine, so the the quality is terrible. I can stream in HD on my laptop on the same wireless network so internet connection speed is not the issue here.

So I figured maybe I could get a better quality if I install an OS which uses very little resources. I am down to two choices, ubuntu netbook edition or xubuntu. I am leaning towards the netbook edition since it is optimized for atom cpus and also it uses a USB drive for installation (I dont have optical drive on this machine).

thank you in advance for all your feedback...

cs

if you need silverlight (I'm assuming netflix) you will need to stick with windows. Linux does not have silverlight support. There are ways around like using a Virtual Machine.. but with that hardware its just not going to run good.

---

### Post by andymorton on 2010-12-22
The netbook edition is the same as the Ubuntu Desktop Edition with the exception of the user interface. So it would be better to go with Xubuntu or maybe even Lubuntu if you don't think your system will be able to handle normal Ubuntu. Having said that my netbook, which also has an Atom processor,  runs the Ubuntu Desktop Edition without any problems. 

andy :)

---

### Post by semetay on 2010-12-22
thank you for the responses. the site I am trying to watch has silverlight and windows media player options. I mentioned silverlight (since it is dynamic) to prove that the cpu is the bottleneck. I think the question is which distro (maybe I should add winxp to the comparison) has the lowest cpu consumption?
            
If only difference between regular ubuntu and netbook edition is the interface than the choice would be xubuntu.now I need to find a way to put xubuntu on a usb stick.

any other thoughts? thanks again

cs

---

### Post by erilidon on 2010-12-22
> **semetay said:**
> thank you for the responses. the site I am trying to watch has silverlight and windows media player options. I mentioned silverlight (since it is dynamic) to prove that the cpu is the bottleneck. I think the question is which distro (maybe I should add winxp to the comparison) has the lowest cpu consumption?
            
If only difference between regular ubuntu and netbook edition is the interface than the choice would be xubuntu.now I need to find a way to put xubuntu on a usb stick.

any other thoughts? thanks again

cs


I'm sure some around here will disapprove but I you want a low cpu load I'd recommend DSL -> [http://www.damnsmalllinux.org/.]("http://www.damnsmalllinux.org/")

If you are wanting to stick with the ubuntu distros then yeah, xbuntu as the only difference in the netbook is the interface (honestly I don't like the interface).

---

### Post by bodhi.zazen on 2010-12-22
> **erilidon said:**
> I'm sure some around here will disapprove but I you want a low cpu load I'd recommend DSL -> [http://www.damnsmalllinux.org/.]("http://www.damnsmalllinux.org/")

Why would someone disapprove ? It is a good distro and solid advice.

I would add Slitaz , I prefer it over DSL or puppy (the 3 light weights).

> If you are wanting to stick with the ubuntu distros then yeah, xbuntu as the only difference in the netbook is the interface (honestly I don't like the interface).

I personally prefer xfce (xubuntu) on my atom netbook. I usually perform a minimal install and add only applications I need.

You can also use light weight applications (vim or gedit rather then open office, etc).

Also, the opensource version of Silverlight is Moonlight:

[http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

> Moonlight is an open source implementation of Silverlight ([http://silverlight.net](http://silverlight.net)), primarily for Linux and other Unix/X11 based operating systems. In September of 2007, Microsoft and Novell announced a technical collaboration that includes access to Microsoft's test suites for Silverlight and the distribution of a Media Pack for Linux users that will contain licensed media codecs for video and audio. 

It does not always work as advertised, and some people object to some aspects, but it is both open source and a viable option.

To install see:

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

Or it is in the Ubuntu repos:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=moonlight&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=moonlight&searchon=name&subword=1&version=all&release=all)

```
sudo apt-get install moonlight-plugin-mozilla
```

Or if you prefer:

```
sudo apt-get install moonlight-plugin-chromium
```

---

