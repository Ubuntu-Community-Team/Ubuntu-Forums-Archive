---
title: "sharing files between computers"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-02-22
I was thinking it would be neat as hell if I could share files between my desktop in the livingroom with my desktop in my bedroom. My computer uses xubuntu while the living room computer is using windows xp. The bedroom desktop also uses a wireless usb adepter to get online and my living room desktop uses a linksys wireless router. How would I go about doing this?

---

### Post by llamabr on 2009-02-22
You'll want to look into samba, and some combination with NFS.  I've never done it, but that should get you started.

Note that I'm not encouraging you to read your man pages, as people here get mad as hell when you suggest that.

but, since you've gotten no replies yet, mine might hopefully get you started on the right path.

if not, feel free to complain about my suggestions to your ubuntu admin.

---

### Post by LunaticHiatus on 2009-02-22
what is this man pages business anyways? I just started hearing people refer to that in a technology forum I vist. No one ever referred to it before though

---

### Post by mkvnmtr on 2009-02-22
I am about to do the same thing. I have got as far as installing samba and am waiting for some cables. In the last few days I have noticed a couple of threads in the forum that seemed to explain how to connect. I am sure a search would find them in the first five pages.

---

### Post by llamabr on 2009-02-22
I read my first man page in 1995.  I find them to be infinately informative.  It's not something we encourage around here, though, as I've been told that they're too complicated for you.

It sounds like you want to run samba, which will make your linux box see your windows box.  You can then mount your windows box using nfs.  I suspect that they're both pretty easy to install and set up.

---

### Post by yther on 2009-02-22
"[Man pages]("http://en.wikipedia.org/wiki/Man_page")" are the documentation that is installed with most *nix software.  They are basically text with a bit of simple formatting.  Say you want to know the possible options for the "ls" command, well you would go to a terminal and type "man ls".  (In Konqueror you can also type "man:ls" in the address field; there's probably a similar feature in Gnome somewhere.)

A slightly more advanced tool is "info"; it is a hypertext system, so one page may have links to another page, there is a table of contents and hierarchical structure as well.  On Ubuntu, it seems most tools do not have info pages installed, but that's not true on many other distributions.

Programs may also have other sorts of documentation installed, usually to /usr/share/doc/, and it may be in HTML or other forms.

Now, back on topic, I think most Ubuntu systems should already have Samba support built in, so accessing files on a Windows shared folder should be easy.  You could install a Samba *server* on your Linux box(es) and that would enable all of them, including the Windows one, to share files that way.  There's also NFS, but don't ask me about that; I did set it up once, many years ago, but it was not fun and never worked well, so I must have done something wrong.  :P

---

### Post by HermanAB on 2009-02-22
The easiest way to share files with another computer is good old fashioned FTP.  On Windows, use FileZilla (Server and client available).  On Linux use vsftp server and Nautilus or gftp as client.

The second easiest way is NFS, as described here:
[http://aeronetworks.ca/nfs-howto.html](http://aeronetworks.ca/nfs-howto.html)

The hardest way is using Windows networking with Samba.  On Windows, simply mark a folder as Shared, then go look for it with Nautilus or Konqueror on Linux.  To share a Linux folder, you  need to install Samba.  Some Samba help here:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Hope that helps!

Herman

---

### Post by halitech on 2009-02-22
You may want to do some reading here 

[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

the one thing alot of people don't take into account is Xubuntu does not have all the same features as Ubuntu so setting it up is different (no network support in Thunar for browsing)

---

### Post by sERAPHIM_newbie_at_linux on 2009-02-22
Hi hi,

I tackled this problem myself just recently and I found using a Samba GUI is fairly straightforward and easy.

See thread 
[http://ubuntuforums.org/showthread.php?t=1074042](http://ubuntuforums.org/showthread.php?t=1074042)

Cheers

---

### Post by pdtpatrick on 2009-02-22
[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

