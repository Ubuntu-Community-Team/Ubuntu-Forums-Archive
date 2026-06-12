---
title: "Installing without the internet"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by sphambrey on 2011-01-29
Hey Guys!

I'm a complete Linux Newbie, having spent far too long using windows.  I have recently installed Ubuntu 9.04 (old, I know) as a dual boot, on a separate hard drive, alongside XP. (XP won't even acknowledge the second hard drive is there anymore, it's like it's had a strop!)  

Anyhow, my question is this; as great as I'm finding the new experience, the packages that come on the live cd are rather limited in number, so I'd like to install more.  The thing is, I don't have an internet connection on the computer on which it is installed.  Is there a way I can download a package (and it's relevant dependencies on a windows (7) pc and then install them on my pc?

Any help you could give would be appreciated!!

---

### Post by SaintDanBert on 2011-01-29
You can find many more packages on the live-DVD than the live-CD ... if you have a DVD drive and some way to get the other media. How did you get your 9.04 edition the first time?

You say that you don't have the internet.  If you go to most libraries, you can browse the internet and download files to one
of any USB connected storage devices. You might also do the same thing at an "internet cafe" or similar.

The end result is that you have folders on USB or flash storage that will contain some number of *.deb package files.  You could then use **dpkg** or **aptitude** or **apt-get** to install packages from those folders.

You could even get the DVD-ISO file for your favorite edition of Ubuntu. Once you burn the media, you can configure **Synaptic** to use that media as a repository.

Bonne chance,
~~~ 0;-Dan

You could then burn a

---

### Post by Tengen Toppa tux on 2011-01-29
my friend has a similar problem, there are some pacages that you can download at your local library and transport via tumb drive or other media to your computer, or you can get a more advanced linux, a different distro maybe? someone who has already added a lot of things to it

---

### Post by sphambrey on 2011-01-29
That's great, thanks guys. Do you have any urls that i can get the packages from? Also can't remember where i got the live cd from, where could i get the 10.10 dvd from?

---

### Post by SaintDanBert on 2011-01-29
> **sphambrey said:**
> That's great, thanks guys. Do you have any urls that i can get the packages from? Also can't remember where i got the live cd from, where could i get the 10.10 dvd from?

You can get all sorts of distro downloads here:
[url]http://iso.linuxquestions.org/[/b]

You can also track them down in the respective project web sites.

Bonne chance,
~~~ 0;-Dan

---

### Post by sphambrey on 2011-01-30
Thanks for the info guys. One more question... Can I use an up to date distro of a different Linux (fedora for example) to update my Ubuntu with later libraries?

---

### Post by SaintDanBert on 2011-01-30
Yes, but it might be like adding Chrysler parts to a Ford (choose two unrelated car families of your choice)

Odd are, any "library" or "package" that you seek is available in the repositories of YOUR distribution.  It is pretty rare that a package is "Fedora only" or "Ubuntu only" or similar. Rare does not mean "it never happens" because it does. Some package gets created within one distro family and does good things. Word spreads. For a while, the rest of the world will rely on a tar-ball but eventually, a package appears for your favorite distro.

Use **synaptic** under *buntu and "search" for the package.  Alternately, you might need to learn the package name from search engine results (google, etc) and carry the details into Synaptic.

bonne chance,
~~~ 0;-Dan

---

