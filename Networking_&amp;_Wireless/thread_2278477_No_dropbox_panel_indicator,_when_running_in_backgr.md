---
title: "No dropbox panel indicator, when running in background"
date: 2015-05-07
forum: Networking &amp; Wireless
---

### Post by Kurt_Alan on 2015-05-07
My Dropbox icon on Xubuntu 14.04 LTS has failed to appear since about October, 2014.

I have found no solution to this problem either at this forum or at the dropbox forum.

Of course, without the icon, you have no access to dropbox's preferences, such as the powerful "selective sync" tool.

Dropbox still functions, passively, and you can see its status via CLI but, without the ability to deselect, it is severely crippled. I'm bitter because I'm spending a lot of money . . . 

I have received responses from dropbox support: "no solution at this time." 

What I call my "long-ass workaround" is that I dual-boot Xubuntu 14.04 with Ubuntu 14.04. On Unity DE, the indicator (and menus) work as they should.

In Xubuntu, I maintain a limited set of files, mostly documents. In Unity, I have my full data feature set which I can manipulate as I choose . . . 

I am grateful that Dropbox supports Linux.  But my fav DE is Xubuntu, so this is a disappointment.

---

### Post by Kurt_Alan on 2015-05-08
I just received a strong response from Dropbox Tech Support. I am applying these solutions now and will report back. This letter contains information that others might find useful:


Ticket #3008452: DB: May 2015 Re-Visit: Dropbox Icon FAIL on Xubuntu 14.04 LTS
You can add a response by replying to this email.

Please be sure to reply with the same email address that you used to originally contact us.


Harley, May 7, 8:49 PM:
Hi Kurt!

Thanks for writing in. My name is Harley, and I'd be happy to assist you with this.

When new versions of the Dropbox desktop application are released, issues can arise on computers that use Linux because of the difficulty of testing the latest version on all of the distributions of Linux that exist.

For your computer with Xubuntu 14.04, I'm going to give you the steps to perform a complete uninstall of Dropbox, then install the latest stable release of our software. Hopefully this gives you full functionality again, but if you're still only able to access Dropbox through the command line then we have directions on how to manage selective sync settings in a headless environment here: [https://www.dropbox.com/en/help/175](https://www.dropbox.com/en/help/175).

First, make sure you save and quit ALL programs that access files in the Dropbox folder.

Depending on your OS and the package you used to perform the installation, you could have files in two different locations. I'm sending you instructions for both of the cases, so if some of the commands error out don't worry.

Run the following commands in your terminal:

&#8194;&#8194;&#8194;&#8194; dropbox stop
&#8194;&#8194;&#8194;&#8194; dropbox status&#8194;&#8194;# Should report "not running"
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox-dist
&#8194;&#8194;&#8194;&#8194; rm -rf /var/lib/dropbox
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox*
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove nautilus-dropbox
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove dropbox
&#8194;&#8194;&#8194;&#8194; rm /etc/apt/source.d/dropbox

After this, you can download version 3.4.6 of Dropbox at your command prompt. Depending on your system, you'll need either the 32-bit or 64-bit installer files.

32-bit installer:

cd ~ && wget -O - "https://d1ilhw0800yew8.cloudfront.net/client/dropbox-lnx.x86-3.4.6.tar.gz" | tar xzf -

64-bit installer:

cd ~ && wget -O - "https://d1ilhw0800yew8.cloudfront.net/client/dropbox-lnx.x86_64-3.4.6.tar.gz" | tar xzf -

Next, run the Dropbox daemon from the newly created .dropbox-dist folder to install the application:

~/.dropbox-dist/dropboxd

More installation and CLI information is also available here:

&#8194;&#8194; [https://www.dropbox.com/install](https://www.dropbox.com/install)

After doing this, you should have a working version of Dropbox on your Linux system. But if this installation of Dropbox did not resolve your issue, please let me know so we can continue troubleshooting.

I hope this helps!

Have a wonderful day!
Harley

---

### Post by Kurt_Alan on 2015-05-15
> **Kurt_Alan said:**
> I just received a strong response from Dropbox Tech Support. I am applying these solutions now and will report back. This letter contains information that others might find useful:


Ticket #3008452: DB: May 2015 Re-Visit: Dropbox Icon FAIL on Xubuntu 14.04 LTS
You can add a response by replying to this email.

Please be sure to reply with the same email address that you used to originally contact us.


Harley, May 7, 8:49 PM:
Hi Kurt!

Thanks for writing in. My name is Harley, and I'd be happy to assist you with this.

When new versions of the Dropbox desktop application are released, issues can arise on computers that use Linux because of the difficulty of testing the latest version on all of the distributions of Linux that exist.

For your computer with Xubuntu 14.04, I'm going to give you the steps to perform a complete uninstall of Dropbox, then install the latest stable release of our software. Hopefully this gives you full functionality again, but if you're still only able to access Dropbox through the command line then we have directions on how to manage selective sync settings in a headless environment here: [https://www.dropbox.com/en/help/175](https://www.dropbox.com/en/help/175).

First, make sure you save and quit ALL programs that access files in the Dropbox folder.

Depending on your OS and the package you used to perform the installation, you could have files in two different locations. I'm sending you instructions for both of the cases, so if some of the commands error out don't worry.

Run the following commands in your terminal:

&#8194;&#8194;&#8194;&#8194; dropbox stop
&#8194;&#8194;&#8194;&#8194; dropbox status&#8194;&#8194;# Should report "not running"
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox-dist
&#8194;&#8194;&#8194;&#8194; rm -rf /var/lib/dropbox
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox*
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove nautilus-dropbox
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove dropbox
&#8194;&#8194;&#8194;&#8194; rm /etc/apt/source.d/dropbox

After this, you can download version 3.4.6 of Dropbox at your command prompt. Depending on your system, you'll need either the 32-bit or 64-bit installer files.

32-bit installer:

cd ~ && wget -O - "https://d1ilhw0800yew8.cloudfront.net/client/dropbox-lnx.x86-3.4.6.tar.gz" | tar xzf -

64-bit installer:

cd ~ && wget -O - "https://d1ilhw0800yew8.cloudfront.net/client/dropbox-lnx.x86_64-3.4.6.tar.gz" | tar xzf -

Next, run the Dropbox daemon from the newly created .dropbox-dist folder to install the application:

~/.dropbox-dist/dropboxd

More installation and CLI information is also available here:

&#8194;&#8194; [https://www.dropbox.com/install](https://www.dropbox.com/install)

After doing this, you should have a working version of Dropbox on your Linux system. But if this installation of Dropbox did not resolve your issue, please let me know so we can continue troubleshooting.

I hope this helps!

Have a wonderful day!
Harley

**OP Update**

The uninstall and reinstall FAILED -- still no indicator and, therefore, no menu or selective sync access.

I replied to above email, my case was escalated, and this is the new response:

Frida, May 12, 2:21 PM:

Hi Kurt,

My colleague Harley escalated your request to me and I will be assisting you moving forward. My name is Frida and I'm a member of our team who specializes in desktop application issues.

After reviewing the issue you described, it appears that your specific desktop environment of Linux may not be supported by our desktop application. Xubuntu may be supported but you have to make sure that certain dependencies are installed. Please review the "For Advanced Users" section at the bottom of this article for detailed information about this:

[https://www.dropbox.com/en/help/3](https://www.dropbox.com/en/help/3)

You need to make sure that the dependencies are also updated along with the Dropbox desktop application - if you're unsure about this, please reach out to Xubuntu support directly.

I hope this is helpful - please let me know if you have any other questions.
Regards,

Frida

Further:

For our advanced users

Linux installer

Dropbox supports the following desktop environments:
Ubuntu (Unity) and GNOME Classic, full support using the package in our*installation page.

XFCE is supported if the corresponding Nautilus dependencies are installed.
GNOME shell natively displays the file overlays, but requires the extension TopIcons to get the application indicator (tray icon).

Dropbox uses*QT 5.3, and as such needs the following software to work on desktop environments:

GTK 2.12 or higher
GLib 2.22 or higher
Libnotify 0.4.4 or higher
Libappindicator 1.0
Nautilus 2.30.0 or higher

The Nautilus installer source code has been released under an MIT license, and people have reported building from source on different versions of Gentoo, Arch Linux, OpenSUSE, and Debian. Your results may vary.

CONCLUSIONS

DE Xubuntu (Xfce) does NOT have Dropbox full support. (I can confirm that Dropbox works perfectly "out of the box" in Ubuntu DE Unity).

Can you confirm this? **Whereas Dropbox now requires QT 5.3, Xubuntu 14.xx does NOT** **support QT 5.3**. But it appears that if you can satisfy the dependencies for QT 5.3, that Dropbox MAY work on Xubuntu.

I opened Synaptic and searched Dependencies and found that GLib, Libnotify, and Libappindicator were already installed. However, Gtk was not installed. Not being sure which Gtk to install (there were many), I installed gtk-3-examples and gtk3-engines-xfce.  After a reboot, I still have a Dropbox fail -- no indicator.

I AM LOOKING FOR SOMEONE!

Is there anyone here with Xubuntu and the same issue as above that wants to add to this post to see if we can't fix this problem once and for all?

---

### Post by vasa1 on 2015-05-15
Kurt, you may get more views if you ask a mod to move your issue of Dropbox and **Xubuntu** to a separate thread. The original thread is tagged with [Debian]. Xubuntu users may give this thread a miss.

---

### Post by Kurt_Alan on 2015-05-15
> **vasa1 said:**
> Kurt, you may get more views if you ask a mod to move your issue of Dropbox and **Xubuntu** to a separate thread. The original thread is tagged with [Debian]. Xubuntu users may give this thread a miss.

Thank you, vasa1. How do I ask a mod to do this?

---

### Post by vasa1 on 2015-05-15
> **Kurt_Alan said:**
> Thank you, vasa1. How do I ask a mod to do this?
Click on the "Report" button in the lower left corner of your post (or anyone else's) and ask for what you want.

---

