---
title: "Reliable Email Application?"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by demarshall on 2010-12-30
Over the past few years I have, at various times, used both Evolution and Thunderbird having had problems with both of them.

I have several email accounts which I access through IMAP and have received error messages in both apps when they had been working fine for hours or perhaps days before.

I have contacted my server provider and all that they suggested was to use their SMTP rather than my ISP's. That had worked for a time but then caused problems so I set it back. Then the problems began again.

I hate the fact that Evolution will not allow me to check one email account without checking them all...

I have two questions...

What is the most reliable IMAP capable email client for Ubuntu 10.04?

How do I determine whether the problem is on my end or my server's end?

Thanks for any assistance. I'm not really a newbie as far as the amount of time that I've been using Ubuntu but feel that way with simple problems like this...

Presently using Evolution 2.28.3 and whatever the newest Thunderbird (afraid to start it again because of so many error messages)

---

### Post by rockerphil on 2010-12-30
i know when i was using an email client i tried several, and i personally liked Claws mail, it should be in the repos, but doesn't natively support HTML and all those other nusences, but can be supported through various plugins, and to put the perverbial icing on the cake it's extremely lightweight. just a suggestion, and i hope this helps,

Phil

---

### Post by demarshall on 2010-12-30
Thanks Phil but I think I need a more feature-rich client.

David

---

### Post by HermanAB on 2010-12-30
Howdy,

I still have to meet a bug free email client.  Your choice of poison is Kmail, Evolution and Thunderbird, so maybe you should try Kmail.

I use both Thunderbird and Evolution on a daily basis and once in a few years Kmail.  They all mostly work.

---

### Post by demarshall on 2010-12-30
Thanks Herman.  :-)

Perhaps it's time that somebody wrote an email client that would do more than "mostly work". One would think this would be a priority since email is such a necessary part of everybody's life.

After using Windows 7 on my netbooks, I almost feel like switching except for some of the reasons that I initially switched to Linux on my desktop machine...

Security and Freedom - still words that Microsoft doesn't seem to understand...

---

### Post by Andrew Jeyaraj on 2010-12-30
i also have been having problems with Evolution. Try SpiceBird:
[http://www.spicebird.com/download](http://www.spicebird.com/download) and 

Sylpheed :[http://sylpheed.sraoss.jp/en/download.html](http://sylpheed.sraoss.jp/en/download.html)

---

### Post by shuttleworthwannabe on 2010-12-30
> **Andrew Jeyaraj said:**
> i also have been having problems with Evolution. Try SpiceBird:
[http://www.spicebird.com/download](http://www.spicebird.com/download) and 

Sylpheed :[http://sylpheed.sraoss.jp/en/download.html](http://sylpheed.sraoss.jp/en/download.html)

Spicebird looks kinda interesting--I will try that; any .deb package for this? tarballing is going to give me a challenge.

S

---

### Post by crichard on 2010-12-30
> **shuttleworthwannabe said:**
> Spicebird looks kinda interesting--I will try that; any .deb package for this? tarballing is going to give me a challenge.

S

Installation is simple, you can follow the similar tutorial here, [Installing Firefox and Thunderbird in Ubuntu ]("http://surferzworld.com/2010/01/installing-firefox-thunderbird-ubuntu/")

Try the same steps & use spicebird instead of firefox on the terminal command,
```
sudo mv ~/spicebird /opt && sudo ln -s /opt/spicebird/spicebird /usr/bin/spicebird
```

However, this is my mail client migration path,
Thunderbird ->  Evolution -> [Opera mail]("http://www.opera.com/mail/") (Opera browser's built-in e-mail client) 
Try out Opera. :)

---

### Post by oldos2er on 2010-12-30
What error messages are you receiving?

---

### Post by demarshall on 2010-12-30
> **Andrew Jeyaraj said:**
> i also have been having problems with Evolution. Try SpiceBird:
[http://www.spicebird.com/download](http://www.spicebird.com/download) and 

Sylpheed :[http://sylpheed.sraoss.jp/en/download.html](http://sylpheed.sraoss.jp/en/download.html)
Spacebird sounds interesting but I don't like the idea of installing from source for a few reasons.The biggest one is How can you uninstal and keep track of apps installed from source? Is it possible to take an uncompiled app and create a .deb file from it?

---

### Post by cipherboy_loc on 2010-12-30
> **demarshall said:**
> Spacebird sounds interesting but I don't like the idea of installing from source for a few reasons.The biggest one is How can you uninstal and keep track of apps installed from source? Is it possible to take an uncompiled app and create a .deb file from it?

Here are two Launchpad PPAs, the first being a testing version, the second one being stable:


[https://launchpad.net/~spicebird/+archive/ppa](https://launchpad.net/~spicebird/+archive/ppa)

[https://edge.launchpad.net/~lil.wk/+archive/ppa](https://edge.launchpad.net/~lil.wk/+archive/ppa)


Cipherboy

---

### Post by stmiller on 2010-12-30
> **oldos2er said:**
> what error messages are you receiving?

++

?

---

### Post by demarshall on 2010-12-30
> **demarshall said:**
> Spacebird sounds interesting but I don't like the idea of installing from source for a few reasons.The biggest one is How can you uninstal and keep track of apps installed from source? Is it possible to take an uncompiled app and create a .deb file from it?
I briefly checked out Opera Mail and it seems to lack one of the abilities that I use a lot and that is standard labelling of messages. It has labeling but semms to lack the ability to remove those labels once a message has been dealt with.

---

### Post by crichard on 2010-12-30
> **demarshall said:**
> I briefly checked out Opera Mail and it seems to lack one of the abilities that I use a lot and that is standard labelling of messages. It has labeling but semms to lack the ability to remove those labels once a message has been dealt with.

Adding, removing & modifying labels are just a click away. Have you tried it on Opera 11? It's better than earlier versions..

---

### Post by demarshall on 2010-12-31
> **crichard said:**
> Adding, removing & modifying labels are just a click away. Have you tried it on Opera 11? It's better than earlier versions..
I did install Opera 11 and saw how to label messages but it was unlike what I was used to... icons rather than colors... I don't believe that IMAP actually supports that kind of labelling.

I could not see a way of removing the labels either.

---

### Post by crichard on 2010-12-31
> **demarshall said:**
> I did install Opera 11 and saw how to label messages but it was unlike what I was used to... icons rather than colors... I don't believe that IMAP actually supports that kind of labelling.

I could not see a way of removing the labels either.

I've not used IMAP in my configuration, every mails (10 e-mail ids) are configured in POP3. So, I don't know how labels work with IMAP. However, you mentioned about removing labels. 
[LIST]To delete a Label, Select the label in the Mail panel(F4) & press Delete, then Enter to confirm the deletion. 
[/LIST]
[LIST]To remove the existing Label to a mail, select the Mail in the Message list & click on the Label, then uncheck that particular Label.
[/LIST]

---

### Post by Kellemora on 2010-12-31
Hi demarshall

I'm still using the Windows version of Eudora Pro.....

The only problem with using it, running it in WINE of course, is that you have to go to the attachments folder via Ubuntu in order to view PDF files and the like, unless you install a Windows PDF reader in WINE, and hope it works from there.  But since I'm usually printing the PDF files I receive I keep a linked copy of the Attach Folder on my desktop.

Thunderbird may look like Eudora, but works NOTHING like Eudora, it's still Thunderbird with a pretty cover is all.

I have all of my e-mails sorted and categorized from around 1980 forward.
I can read them using a text editor if necessary.  But they are all easily accessible in Eudora also.

I can't say the same about MOST of our Program Generated Archives, EG. Income Tax Records 1977 through 1990, because the programs change what they read and how they read them.  So, it was back to Windows 3.11 to retrieve and update to Windows 95, then to retrieve and update to Windows 98, then to retrieve and update to Windows XP, then over to Linux Open Office where ALL of our data archives could be saved as PDF files with backup as simple image files.

We had over 100,000 .wri and .pcx files that Windows no longer recognized.
After moving to Linux, ALL of these old useless but important archives were retrieved and updated to current and much smaller file sizes, that could be read by virtually any editor or image viewer.

But archives being accessible is my primary reason for sticking with Eudora all these decades.....  They don't make it any more!  But e-mail has not changed much either.  AND Eudora has features I've NEVER FOUND in any other e-mail program.  The primary one I use 50 times a day is the SEND AGAIN feature.  This is NOT a FORWARD feature as used by other e-mail programs that louse up e-mails that are Forwarded a few times.
SEND AGAIN does NOT ADD ANYTHING to the original e-mail, like tabs or spaces, etc. or add info to the Subject line either.

Give Eudora a try, I've never found anything better!
You can't get the Pro version as they will NOT accept money anymore, but I think it unlocks without a payment now too!

TTUL
Gary

---

