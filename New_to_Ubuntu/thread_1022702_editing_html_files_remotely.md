---
title: "editing html files remotely"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by dazwest on 2008-12-27
Morning all
I've just set up ubuntu on my laptop and also on my desktop. I'm using my desktop as a server and accessing it from my laptop from around the house and roaming around too.

Whats the best way of editing html/php files on my server?
Do I share the www folder and just open, edit and save the files there?
Do I set up FTP client/server and ftp files to/from the server?
Should I use ssh and edit the files on the server itself?

Any and all opinions appreciated!

D

---

### Post by tibellus on 2008-12-27
Hello!

In my opinion, SSH is the best way to do it, as it provides the most secure way of editing those files. And you don't have to go through a lot of configuring to have access to your server.

Let's see what others think, though. :)

---

### Post by scragar on 2008-12-27
Personaly I would edit the files localy, and FTP them back up, but what do I know, I only do that stuff for a living :p

The easiest method is to use something like quanta, and just open the file directly through FTP(which means it downloads it, then uploads it as you save it), this causes some nasty latency though, it's much easier to do the uploading yourself, manualy.

---

### Post by namdung on 2008-12-27
All the three methods looks fine.

But if ur PC is connected to the Internet or n/w, then I don't suggest u share ur folder for security reasons.

Does ur PC have GUI installed? If not, ssh method will be inconvenient.

FTP method ensures that u have a local copy in ur laptop as backup.

Take ur pick.

Good luck!!!

---

### Post by HereInOz on 2008-12-27
I would tend to edit the files locally, then upload once you are sure that they are fine.  I have never liked the idea of remote live editing of website or database files - you have no "oops" factor left to you.

FTP the files to your local machine, edit them, then FTP them back up.  It also means you have a backup of your website on your local machine.  Not a bad thing either.  

It is not advisable to share the website folder.

---

### Post by dazwest on 2008-12-27
Many thanks all for your answers.
OK, I'm gonna go with the consensus and use the FTP method.

So the follow on question is what do you recommend for FTP client/server and HTML/PHP editor?

cheers!

---

### Post by HereInOz on 2008-12-27
For the FTP server, you can install proftp - in the repos - and if you don't want to play in the proftp config file, install gproftp which gives you a gui to configure your ftp server.  

The default ftp location with gproftp is /var/ftp.  You will probably want to change that to your www directory.

---

### Post by bwallum on 2008-12-27
I use gFTP (in the repos) all the time for maintaining web sites.

---

### Post by tibellus on 2008-12-27
As HTML/PHP editor I would recommend Geany. It's available in the repositories, but if you want to get the latest version, you can find it [**here**]("http://www.geany.org/").

---

### Post by jimcooncat on 2008-12-27
I've got a few websites I update infrequently for my boss and clients. I'm in agreement with the above posts, and here's what I do.

1. Use SSH connections whenever it's available. 

2. Get to know your transfer software well. I use

  [INDENT]a. gFTP on Linux (does SSH transfers also)

  b. WinSCP on Windows (does FTP transfers also)

  c. Now that I'm getting better at it, I'm moving towards doing my connections with FUSE -- the remote directories look like local ones.

  d. Many people use synchronization software instead, so they don't have to remember which files they edited.[/INDENT]

3. Do your editing on your local machine. Install a simple backup, and backup before you start your editing session. 

4. Install Apache (or a full LAMP if you do PHP) on your local machine, and test your new draft website before you upload.

5. Test your drafts with a few browsers to make sure that things work the way their supposed to before you overwrite your working website.
[INDENT]  a. IE4Linux works well for me to test the most used browser. I only use it to look at my own websites, for safety reasons.

  b. Firefox, of course.

  c. Epiphany-webkit. I haven't got this yet, but I will when I do my next update. The rendering should be similar to what MAC and KDE users would see, without installing Konqueror and all it's dependencies.

  d. Opera.

  e. Text based browser like elinks.[/INDENT]

6. Keep your website simple. Learn to do simple HTML and embellish with CSS. Use Flash and other plugins only where they make sense. Don't forget about mobile and dialup users. Don't distract your audience with fluff, they want your content -- think about a beautiful girl adding makeup to enhance, not cover up her features.

7. Use relative links (/about/index.html) not full links ([http://mywebsite.com/about/index.html](http://mywebsite.com/about/index.html)) to keep your flexibility when pointing to stuff on your own website. You never know when you might need to change your hostname. For your case, you might get tired of hosting on your desktop and want to upload your site to a shared host.

---

