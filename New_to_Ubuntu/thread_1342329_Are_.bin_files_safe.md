---
title: "Are *.bin files safe?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by WestCity on 2009-11-30
Hi, I downloaded "GoogleEarthLinux.bin" from here: [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)
I know, it will sound like paranoia...but, I don't like Google. I think they are spying us, collecting information, etc. So, how do you think - is it safe to use this program? I've read, what once you make a bin file executable and install it, program can make any changes it wants to make to your system...

---

### Post by whoop on 2009-11-30
Short answer: bin files are not safe...

---

### Post by NoaHall on 2009-11-30
> **whoop said:**
> Short answer: bin files are not safe...

I disagree. Most are safe, as long as you download from official, well known, safe sites.

---

### Post by themusicalduck on 2009-11-30
Since it's from google, you can probably assume it's safe. Whether you trust google enough is really up to you.

Having said that, apparently it's possible to install Google Earth using the medibuntu repository according to this page - [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Which at least means it'll be easier to remove if you want to rather than use a bin file.

---

### Post by bodhi.zazen on 2009-11-30
That is a very broad question.

bin files are generally written by people who do not want to be bothered to write a rpm or .deb , eithere because they do not have the knowledge or time (or both). With that said, I am sure some .bin files are well though out.

Since they are from a third party they are not officially supported here, although some may have some experience with them, depending on the source.

When installing 3rd party apps , you can only trust them as much as you trust the source. do you trust Google. ?

---

### Post by lykwydchykyn on 2009-11-30
> **bodhi.zazen said:**
> That is a very broad question.


Almost broad enough to be meaningless, I'd say.  File extensions really don't mean much in Linux; the desktop environment might use them for application association purposes, but they don't really affect what's in the file or what the system does with them.

By convention, .bin files are usually executable files of some kind, but that's not always true.

You might as well ask, "are files that start with 'b' safe?"

---

### Post by Axos on 2009-11-30
Any software you install can do anything you can do. That is, it can read any file you can read, write to any file to which you can write, and connect to any computer on your LAN or the Internet to which you can connect. It can also collect all your keystrokes.

This goes for all the software in Ubuntu, whether you install it from a bin file, a .deb file, the Ubuntu CD, or the repository. All software can do anything you can do.

---

### Post by Paqman on 2009-11-30
Google Earth is available from the [Medibuntu]("http://www.medibuntu.org/") repository. Installing from a repo is better than installing a random download from a website for a whole lot of reasons.

---

### Post by whoop on 2009-11-30
> **NoaHall said:**
> I disagree. Most are safe, as long as you download from official, well known, safe sites.

I did not answer the question if I personally find it safe enough to install a bin file from google, or a repository I trust, because I do. It wasn't a consideration.

I was answering the question: are *.bin files safe?
A binary executable program is not safe; even if most binary executable programs are not malicious (and considered safe). 
An ascii text file, or a jpeg etc., those are safe (for now). Source code could be considered safe (to extent).

If you trust a certain repository, company or individual, you trust that the software it provides is not intentionally malicious (although sometimes they are), however they still can be unintentionally malicious. It can be a hazardous bug (I remember a bug that could waste your ethernet card in an ubuntu alpha release, could be pre-alpha), or the repository could be altered from an outside source (Ubuntu repositories where hacked a while back).

I have no problem installing bin files from google, or updating via the repositories. I consider them safe, yet I can't say bin files are safe.
It al depends on how much paranoid you are or want to be :D

---

### Post by sisco311 on 2009-11-30
> **bodhi.zazen said:**
> 
When installing 3rd party apps , you can only trust them as much as you trust the source. do you trust Google. ?

+1

It's true that Google collects some type of information, but that's not a secret, so they are not spying. 

If you don't agree with their [Privacy Policy]("http://www.google.com/privacypolicy.html"), then don't use services and/or software provided by Google.

---

### Post by WestCity on 2009-12-01
Mhm, thanks for the answers. I'll install it. ;)

---

