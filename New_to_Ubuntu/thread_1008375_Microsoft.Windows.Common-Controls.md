---
title: "Microsoft.Windows.Common-Controls"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by AmberG on 2008-12-11
Hi more noob puzzlement ;)

I'm attempting to install Navicat on Ubuntu 8.10

I have a problem - it won't install
I hav contacted Navicat and they responded with have a look at their error log.  which I have passed back to them ... and am awaiting a response... 

meanwhile I though I might ask here (experts on Ubuntu) as I'm of the impression that it is not just a Navicat issue and I am probably not alone.

I get the error message

fixme:actctx:parse_depend_manifests Could not find dependent assembly
L"Microsoft.Windows.Common-Controls"
X Error of failed request: BadRequest (invalid request code or no such
operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 10
Current serial number in output stream: 10

so I guess I'm missing "Microsoft.Windows.Common-Controls"
what is it and where do I get it and why

BTW I have WINE installed and working.

---

### Post by Paqman on 2008-12-11
What version are you trying to install?

the [Wine App DB entry for Navicat]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3226") seems like you *should* be ok installing anything except 7.2.6, and even then the tester said it would install.

---

### Post by AmberG on 2008-12-11
> **Paqman said:**
> What version are you trying to install?

Sorry about that - should have said.

It is the one that Navicat recommends/sells for Linux that comes as navicat8_mysql_en.tar.gz direct download from their site. (Not the Lite version)

I have seen the windows version in action and was impressed - I don't have (don't want) MS Windows on this machine (just WINE 1.0.1).

It appears from the way that the above loaded that it still requires WINE - which is not a serious problem if it works - which it doesn't yet.

That review on that linked WINE site is a bit out of date - it doesn't refer to Ubuntu 8.10.

---

### Post by Paqman on 2008-12-12
No, if you're installing the Linux version you don't need Wine.

What is inside that .tar.gz? Is there a readme that contains install instructions? Or an install script (or better yet, a .deb?) Or are you trying to compile it from source?

---

### Post by AmberG on 2008-12-12
That doesn't make much sense to me.
No detailed instructions that I could find just a simple 1,2,3

"Extract the file into anywhere you wish"
so I chose  /etc/navicatesql/
"Open the unziped folder."
it extracts to 2 folders navicat/ and wine/ plus a few files
"Double-click start_navicat to start your Navicat"
nothing happened
Their technical support suggested running it as a shell in terminal which I did.  This resulted in an error log with the message as given above.

Since then they have suggested running an exe file in wine (that produced a whole bundle of odd error messages).  So it appears that it does need WINE to work :(

Has anyone actually got Naavicat to work on Ubuntu 8,10 ?

Oh and no deb file

---

### Post by alicebtoklas on 2008-12-17
Hi,
Just to mention I have the same problem trying to install Navicat 8 Lite on Ubuntu 8.04
I don't have WINE installed. There is neither readme nor .deb files in the unzipped folder.
Thanks for your help

---

### Post by AmberG on 2008-12-18
Yes, for a commercial product the support and ability of the sold product to install is sadly lacking.

I've seen the MS Windows version and it looks like a very good program and well worth the price.

However, I don't think they have their act together with the Linux version.  Installation didn't work, the customer service has been "thin" and still unable to get it to work after over a week. They appear to have given up.  This is astoundingly poor for a product clearly sold as "for Linux".  Even worse, is that it appears that WINE is an essential part of the installation.  So in reallity certainly NOT a product for Linux OS.

It is also a surprise that there is nothing comparable out there given the marketplace for this.

One unhappy bunny :(

---

### Post by handydan918 on 2008-12-18
> **AmberG said:**
> That doesn't make much sense to me.
No detailed instructions that I could find just a simple 1,2,3

"Extract the file into anywhere you wish"
so I chose  /etc/navicatesql/
"Open the unziped folder."
it extracts to 2 folders navicat/ and wine/ plus a few files
"Double-click start_navicat to start your Navicat"
nothing happened
Their technical support suggested running it as a shell in terminal which I did.  This resulted in an error log with the message as given above.

Since then they have suggested running an exe file in wine (that produced a whole bundle of odd error messages).  So it appears that it does need WINE to work :(

Has anyone actually got Naavicat to work on Ubuntu 8,10 ?

Oh and no deb file
You may be the victim of a permissions issue. If you copied this app to /etc and tried to run it as a user, it very well may not work. Typically, executable don't go in /etc anyway. 
Try installing it to your /home/<username> directory, where youy should have full permissions.

---

### Post by AmberG on 2008-12-18
Have since moved it to /usr/local/bin/navicatsql/...
which was a suggestion from someone else.

That had no effect.

I am a user of a small group on the PC and had already changed access to whole tree including and below ../navicatsql/ to the group.

As that had no effect (unsurprising) the ownership of the tree was also changed to self - also without effect.

moving everything to ../home will mean breaking just about every thing here as this area is just used for "personal" items.  There are no other applications in that tree.

Everything has been installed in /etc/... or in /usr/local/... and everything else on the pc appears to work without a problem.

Again the installation notes with the program were of no help.

Thanks for the suggestion though, and I will try it in /home/ being desperate for a fix.

---

