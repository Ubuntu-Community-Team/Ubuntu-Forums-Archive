---
title: "Installing/uninstalling on Ubuntu server"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by SudoTinman on 2010-05-18
I've installed Ubuntu server 10 on a spare computer, and am attempting to install phpmyfaq.de.

At first, I used Git to download and install phpmyfaq, but just found out that Git gave me the most recent version humanly possible...which is in alpha...and I'm new enough to linux without needing any added challenges.

I posted a question to their board about installing a stable version, and was told to download it from the webpage instead of using git.

I'm attempting to run this server without a gui, if I have to, I'll install one and do it that way, but I'd like to keep it lite and pure as possible.  Can someone give me a push in the right direction on how to remove my existing installation, and then download, unpack and install the stable version using the shell?

[http://www.phpmyfaq.de/download.php](http://www.phpmyfaq.de/download.php)

I'm not a troll, and as a result, your help is very much appreciated.

---

### Post by cariboo on 2010-05-19
I just installed phpmyfaq, it's fairly simple, this is what I did.

[list=1]
[*] Downloaded phpMyFAQ 2.6.4 from the website to my desktop system
[*] copied the zip file to the server using sftp
[INDENT]open nautilus, press Ctrl-L type sftp://user@server, [/INDENT]
[*] Installed unzip on the server
[*] Copied the unzipped directory to /var/www
[INDENT]sudo cp /home/user/phpmyfaq-2.6.4 /var/www/faq[/INDENT]
[*] Created the database, install phpmyadim if you haven't already
[*] Created the attachment and data directories
[INDENT]cd /var/www/faq, then sudo mkdir attachment data [/INDENT]
[*] Installed php5-gd
[*] At my desktop system open firefox and typed
[INDENT][http://server/faq/install/setup.php](http://server/faq/install/setup.php)[/INDENT]
[/list]

From there, just fill in the info on the setup page.

**Note:** The above instruction presume you have ssh setup. I did the install remotely from my desktop system.

---

### Post by SudoTinman on 2010-05-20
Thanks cariboo,

I installed a Gui today and downloaded Firefox, downloaded, unzipped and replaced the 2.7 with the 2.64 files.  That went pretty well, but is it Possible to just download the .tar.gz file and extract it directly through the command line?

after the downgrade, I got some of my issues resolved, but am currently trying to get a mail application loaded/working, so I can register new users... any tips on that?

---

### Post by jerome1232 on 2010-05-20
Yes you can even use a cli browser like links2, or w3m, or lynx.

wget is a good tool for downloading files.


But as cariboo said I prefer running the server headless and working from my desktop. Using ssh to control the server remotely. I can find files using firefox on my desktop then either sftp them to the server or wget them to the server.

---

