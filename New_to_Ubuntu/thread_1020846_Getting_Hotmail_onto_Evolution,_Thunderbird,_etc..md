---
title: "Getting Hotmail onto Evolution, Thunderbird, etc."
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-12-24
My main e-mail address is my hotmail one, but I'd like to get them on my local system instead of through a browser.

At the moment, I haven't set up either Evolution or Thunderbird, so I'd appreciate some impartial guidance as to which has what benefits/drawbacks compared to the other, and which (if either) can import my hotmail inboxes with least fuss and bother.

I've used Outlook and Thunderbird on Windows so I have some legacy files to import too.

---

### Post by ieee488 on 2008-12-24
I didn't know that Hotmail has POP3 service.

---

### Post by avanhel on 2008-12-24
For Evolution I do not know what to do but for Thunderbird you can use the webmail extension that you can download from their website. That together with the hotmail extension should allow you to get mail from Hotmail without using their pop 3 server.

---

### Post by st33med on 2008-12-24
You'll need the WebMail's Thunderbird plugin for Hotmail.  [Get the plugin here.]("http://webmail.mozdev.org/installation.html") Once you download it, install the .xpi file by going to Thunderbird and going to Tools>>Plugins and clicking 'Install Plugin' in the pop-up window.  You want to go to the download location of the .xpi (usually your Desktop) and click that.

---

### Post by 2hot6ft2 on 2008-12-24
I get my hotmail thru Thunderbird You'll need the 2 add-on extensions and to set it all up it's really not that hard but naturally they keep changing stuff and you have to change it again. The 2 you'll need are WebMail installed first and WebMail-Hotmail installed second.

When they screw it up you go to Tools Add-ons then WebMail-Hotmail preferences and change it either to or from WebDav <> Hotmail Live. That usually does the trick.

You can get them here. [http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

And you install them in Thunderbird > Tools > Add-Ons > Install one at a time. Other than that the setup is pretty easy.

---

### Post by Roger Allott on 2008-12-25
I've found a HowTo about getting hotmail on Evolution. [http://ubuntuforums.org/showthread.php?t=200408]("http://ubuntuforums.org/showthread.php?t=200408")

But you guys all seem to favour Thunderbird over Evolution. Could someone please explain what the main differences are?

---

### Post by dmizer on 2008-12-25
The biggest bennefit (for me) with Thunderbird is that it's cross platform and easily portable. I have my Thunderbird profile located on my server, and I can sign onto my email from any computer, Windows, Mac, or Ubuntu.

Edit:
If you've been using Thunderbird on Windows, all you have to do is copy the profile over to Ubuntu, and everything will work just as it did in Windows.

---

### Post by Roger Allott on 2008-12-25
Oh well, I've opted for Thunderbird and installed those two xpi files in the order you guys mentioned. I've then set up my webmail (hotmail) account details.

But then, when it goes off to collect my mail, I'm getting this error message:

[IMG]http://62.233.105.201/screenshots/Screenshot-Alert.png[/IMG]

Anyone got any ideas as to what I've done wrong?

BTW, I note that nowhere yet has Thunderbird asked me for my hotmail password. That's odd, isn't it?

---

### Post by dmizer on 2008-12-25
Did you have hotmail working in your Windows install of Thunderbird?

Edit:

I'm going to bed now, so here's something for you to check just in case ...
1) In Thunderbird, go to Tools > add-ons
2) Click and highlight "WebMail" and select "Preferences"
3) Are the Pop and SMTP server lights green?
4) If so, make a note of the port numbers. If not, change the port numbers to something higher (mine are 5200 and 5201). You'll have to restart Thunderbird if you make any changes here.
5) Close (restart if necessary and recheck the WebMail server lights if you changed port numbers)
6) Click and highlight "WebMail - Hotmail" and select "Preferences"
7) Make sure "WebDav" is selected
[noparse]8)[/noparse] Close, and close the Add-ons
9) Click Edit > Account settings
10) Click on "Server Settings" for your hotmail account.
11) Make sure the Pop mail server port is the same as what was written in step 4
12) Make sure the Username is your complete hotmail address.
13) Click on "Outgoing server (SMTP)
14) Click on "Hotmail - localhost" and make sure the Port number is the same as the SMTP port you saw in step 4
15) Make sure the "server name" says "localhost" (if either the port or server name is incorrect, edit the server so they read correctly)

---

### Post by Roger Allott on 2008-12-25
> **dmizer said:**
> Did you have hotmail working in your Windows install of Thunderbird?
No. This is the first time I've attempted to get hotmail on a proper email client app.

> **dmizer said:**
> Edit:

I'm going to bed now, so here's something for you to check just in case ...
1) In Thunderbird, go to Tools > add-ons
2) Click and highlight "WebMail" and select "Preferences"
3) Are the Pop and SMTP server lights green?
4) If so, make a note of the port numbers. If not, change the port numbers to something higher (mine are 5200 and 5201). You'll have to restart Thunderbird if you make any changes here.
5) Close (restart if necessary and recheck the WebMail server lights if you changed port numbers)
6) Click and highlight "WebMail - Hotmail" and select "Preferences"
7) Make sure "WebDav" is selected
[noparse]8)[/noparse] Close, and close the Add-ons
9) Click Edit > Account settings
10) Click on "Server Settings" for your hotmail account.
11) Make sure the Pop mail server port is the same as what was written in step 4
12) Make sure the Username is your complete hotmail address.
13) Click on "Outgoing server (SMTP)
14) Click on "Hotmail - localhost" and make sure the Port number is the same as the SMTP port you saw in step 4
15) Make sure the "server name" says "localhost" (if either the port or server name is incorrect, edit the server so they read correctly)

You're a star! Thanks for that. The problem did indeed seem to be related to ports, which default to 110 for POP and 25 for SMTP. I used the ones you're using and ..... hey presto, I've now got an interminable wait until all 1,829 messages in my inbox get downloaded!

---

### Post by Roger Allott on 2008-12-25
I have a residual question regarding Thunderbird.

Having now downloaded all 1,829 of my hotmail emails, I see that they're accessible from two different trees in the left-hand navigation area. One is headed "Webmail - ....hotmail.com" and the other is headed "Local Folders".

Why has it seemingly created two identical folders? Is that Thunderbird's normal behaviour?

Something that may be relevant is that because of limited hard disk space for my /home directory, I chose to store my emails on a separate NTFS partition.

---

### Post by dmizer on 2008-12-25
Well before you do anything, I suggest making a complete backup of your current profile. That way if you mess something up while trying to fix this problem, you won't loose anything.

Create a backup:
1) Locate your profile folder (for example, mine is /home/dmizer/.mozilla-thunderbird/0a1477j1.default/)
2) Copy the entire "somenumber.default" directory to another location.

Now, if you break things and Thunderbird doesn't work anymore or your email disappears, you can simply restore the backup and go on with life.

Once you have a good backup, try looking at your accounts (edit > account settings). Do you have two listings for your hotmail account? If so, try deleting one. Close Thunderbird, and restart it. Is there only one working email folder now?

---

### Post by Roger Allott on 2008-12-26
> **dmizer said:**
> Well before you do anything, I suggest making a complete backup of your current profile. That way if you mess something up while trying to fix this problem, you won't loose anything.

Create a backup:
1) Locate your profile folder (for example, mine is /home/dmizer/.mozilla-thunderbird/0a1477j1.default/)
2) Copy the entire "somenumber.default" directory to another location.

Now, if you break things and Thunderbird doesn't work anymore or your email disappears, you can simply restore the backup and go on with life.

Once you have a good backup, try looking at your accounts (edit > account settings). Do you have two listings for your hotmail account? If so, try deleting one. Close Thunderbird, and restart it. Is there only one working email folder now?
Thanks, but before I do that I've got to solve another problem.

I fired up Thunderbird this morning and the two folders are showing in the left-hand pane, but with no sub-folders! Obviously, the one I need most is the sub-folder titled 'Inbox', but it's completely vanished!

Actually, just as I wrote that I had a bit of a brainwave. As I mentioned, I store my inbox on a separate NTFS partition. It would seem that it is rather important that I 'mount' the drive before launching Thunderbird (or any other app I presume that wants access to data not on / or /home).

Is there some way that I can force Ubuntu to mount this drive (or indeed all mountable drives it can see) upon startup?

---

### Post by Roger Allott on 2008-12-26
> **dmizer said:**
> Well before you do anything, I suggest making a complete backup of your current profile. That way if you mess something up while trying to fix this problem, you won't loose anything.

Create a backup:
1) Locate your profile folder (for example, mine is /home/dmizer/.mozilla-thunderbird/0a1477j1.default/)
2) Copy the entire "somenumber.default" directory to another location.

Now, if you break things and Thunderbird doesn't work anymore or your email disappears, you can simply restore the backup and go on with life.

Once you have a good backup, try looking at your accounts (edit > account settings). Do you have two listings for your hotmail account? If so, try deleting one. Close Thunderbird, and restart it. Is there only one working email folder now?

OK, so I did the backup and tried this. There are not, as far as I can see, two listings for my hotmail account.

I've taken a couple of screenshots to explain my problem, or what I think is a problem.

The first is my main Thunderbird screen. You'll notice that there are two Inboxes. Upon launching, Thunderbird checks for emails to load into the top inbox. Then, when I click on the inbox within 'Local Folders', it goes off again and updates that inbox with what the other inbox just collected!

The second screenshot is of my Account Settings screen. I've highlighted the Local Folders bit to show a) that the 'Remove Account' button is greyed out, suggesting that it's not a distinct account, and b) that I'm storing messages on a separate drive.

---

### Post by bren on 2008-12-26
roger 

get a gmail account
IMAP = freedom to do what you want with your mail

bren

---

### Post by Roger Allott on 2008-12-26
> **bren said:**
> roger 

get a gmail account
IMAP = freedom to do what you want with your mail

bren

Thanks, but I won't do that for the following reasons:
[LIST=1][*]Google started out with a philosophy that was quite similar to that of Ubuntu, but recently they have moved to one that is more similar to Micro$oft. Google bits come pre-installed on most Vista boxes now and getting rid of them and their interrogation of your system is a right pain in the butt. The Google Toolbar was the first incarnation of their philosophy change, IMHO.
[*]Thanks to the great people on this forum, and dmizer in particular, I got my hotmail emails onto my system without too much difficulty in the end.
[*]I've had my hotmail account for many years, and changing to a new email address, telling everyone about it and updating sites with new login info would be too much unnecessary hassle.[/LIST]

---

### Post by dmizer on 2008-12-26
> **Roger Allott said:**
> OK, so I did the backup and tried this. There are not, as far as I can see, two listings for my hotmail account.

I've taken a couple of screenshots to explain my problem, or what I think is a problem.

The first is my main Thunderbird screen. You'll notice that there are two Inboxes. Upon launching, Thunderbird checks for emails to load into the top inbox. Then, when I click on the inbox within 'Local Folders', it goes off again and updates that inbox with what the other inbox just collected!

The second screenshot is of my Account Settings screen. I've highlighted the Local Folders bit to show a) that the 'Remove Account' button is greyed out, suggesting that it's not a distinct account, and b) that I'm storing messages on a separate drive.
Thanks for the screen shot, that's cleared things up.

You'll want to change the "Local Directory" under the "Local folders" to whatever the folder is in /home/you/.mozilla-thunderbird/somenumber.default

Make sure that the "local directory" under your hotmail account's server settings is the one pointing to your ntfs drive. Currently both the hotmail account and the "Local Folders" is pointing to the same place, that's why you are seeing double.

I do not have any NTFS drives, so I do not know how to mount them on boot. I suggest doing a forum search with the terms: mount fstab ntfs

> **bren said:**
> roger 

get a gmail account
IMAP = freedom to do what you want with your mail

bren
Freedom to give up a hotmail account I've had since 1996? (yes, i've really had it since before Microsoft bought it). I've also been using Tunderbird in tandem with the webmail plugin since around 2005. (longer than gmail has been around, and way longer than IMAP has been a feature in gmail)

Sometimes people use an email account because that's what everyone they know sends mail to.

---

### Post by Roger Allott on 2008-12-26
> **dmizer said:**
> Thanks for the screen shot, that's cleared things up.

You'll want to change the "Local Directory" under the "Local folders" to whatever the folder is in /home/you/.mozilla-thunderbird/somenumber.default

Make sure that the "local directory" under your hotmail account's server settings is the one pointing to your ntfs drive. Currently both the hotmail account and the "Local Folders" is pointing to the same place, that's why you are seeing double.
Excellent. That's now sorted it (I think) to be set up exactly right.

---

