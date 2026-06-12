---
title: "webdav via https on xubuntu?"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by prairie_dad on 2007-02-18
In Ubuntu (or should I say in Gnome) I can mount a webdav "share" by going to Places > Connect to Server > and then picking "secure webdav https://" from the dropdown menu.  Is there a way to do that in Xubuntu _other_ than by installing Nautilus (which I'd like to avoid so as to avoid Gnome deps and stick to XCFE.)  Is there a way to mount such a resource in Thunar or some other straight GTK+ way?  

Mac OS X does it via Finder > Go, and it's easy in XP, too.  Just not Xubuntu, which I like because it's so peppy on a 733 P3 with 256 meg RAM that I use sometimes.  Or should I use Xubuntu and just bite the bullet and add Nautilus?   :confused:

---

### Post by robajz on 2007-05-27
> **prairie_dad said:**
> Is there a way to do that in Xubuntu _other_ than by installing Nautilus (which I'd like to avoid so as to avoid Gnome deps and stick to XCFE.)  Is there a way to mount such a resource in Thunar or some other straight GTK+ way?  

Experiencing the same I'm now looking at [http://www.google.ie/search?q=davfs2+ubuntu](http://www.google.ie/search?q=davfs2+ubuntu)
particularly [http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Setting_up_davfs2_with_the_Ubuntu_package](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Setting_up_davfs2_with_the_Ubuntu_package)

and going to try... 

... and it worked! :)

There is a little typo: dpgk-reconfigure should read dpkg-reconfigure

I'm wondering if I could use it with fuse...

---

### Post by Hulky42 on 2007-06-07
Hi All,

Using an Ubuntu Linux Desktop 6.06 LTS '(secure) WebDAV webdisk' via the Internet of your ISP (example of my Dutch XS4ALL.nl ISP):

1. Open the Nautilus 2.14.3 file browser for GNOME ;

2. select File - Connect to Server (pop-up window opens) ;

3a. Select 'Service Type': Secure WebDAV (https) ;

3b. Fill in Server info: webdisk.xs4all.nl/youruserid
	(leave the other four fields blank)
3c.	Push the [Connect] button - new pop-up window opens ;

4a. Fill in your Account's "UserID" and "Password" fields ;
	(optionally) check the both checkboxes:
		- Remember password for this session,
		- Save password in keyring.

4b.	Push the [Connect] button (And...Done!).

Look at your Nautilus File Brouwser now and see the Webdisk at your ISP with the name: "account on webdisk.xs4all.nl".
You can browse the Webdisk (WebDAV protocol via secure https), manage folders and files via the Internet.

---

