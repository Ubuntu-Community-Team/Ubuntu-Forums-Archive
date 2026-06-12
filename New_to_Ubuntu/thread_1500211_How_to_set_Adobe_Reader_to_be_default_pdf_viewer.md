---
title: "How to set Adobe Reader to be default pdf viewer?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by const451 on 2010-06-02
I've just installed Adobe Reader but when I click on pdf file it is still being opened by Evince. How to set Adobe Reader to be default pdf viewer?

THX

---

### Post by friv_livs on 2010-06-02
Preferences->prefered programs.

If you don't get the option in the dropdown menu:
1. See what the package is named in Administration->Synaptic.
2. Search for the /usr/bin or /usr/sbin executable
3. Set the following terminal command in the prefs->prefered programs pdf section:
      . /usr/bin/"executable"
 

Also, how long does it take you to tarball a known amount of GB's?

---

### Post by const451 on 2010-06-02
> **friv_livs said:**
> Preferences->prefered programs.

If you don't get the option in the dropdown menu:
1. See what the package is named in Administration->Synaptic.
2. Search for the /usr/bin or /usr/sbin executable
3. Set the following terminal command in the prefs->prefered programs pdf section:
      . /usr/bin/"executable"
 

Also, how long does it take you to tarball a known amount of GB's?

I went to prefered applications but pdf setting is nowhere to be found. 

The app called acroread, it is located in \bin but it is actually a link to shell script.

I do not understand what you mean in 3, sorry.

I do not quiet understand this either 'Also, how long does it take you to tarball a known amount of GB's?' Tarball means to zip? I haven't done it yet, it's my first week with Ubuntu (or Linux for that matter).

---

### Post by Linuxforall on 2010-06-02
Right click on any PDF, select properties>open with and select adobe, next time all pdf will open with Adobe.

---

### Post by const451 on 2010-06-03
> **Linuxforall said:**
> Right click on any PDF, select properties>open with and select adobe, next time all pdf will open with Adobe.

That does not work - Adobe is on the menu 'open with' - this is how I open pdf files now with Acrobat Reader, however it is not on the list in the dialog box of other applications, meaning I cannot apply that check box 'Use this application to always open pdf files'.

Any other suggestions how to make Adobe Reader to make a default reader for my pdf files, please?

---

### Post by philinux on 2010-06-03
Can you click the add button on the open with dialog?

---

### Post by amitava_1952 on 2011-11-04
It seems to me that the best way to set Adobe Reader as the default for PDF files is as follows.

[LIST=1]
[*]Right-click on any PDF file in the file browser and choose "Properties".
[*]In the "Properties" window, click on the "Open With" tab. You will see a list of applications including "Adobe Reader", with the "Evince" being the selected application.
[*]This is optional. If you do not want to ever open a PDF file with any other application, select each of the unwanted programs and remove it by clicking the "Remove" button at th bottom.
[*]If you do not carry out Step 3, explicitly select the "Adobe Reader" entry.
[*]Click the close button to close the "Properties" window.
[/LIST]
That should do it.

---

### Post by chintanp on 2011-12-18
I followed the first step..but the option of Adobe Reader is nowhere to be found ion the list of all applications in the "Open With" tab in properties. Any idea how I can add Adobe Reader there..? Adobe Reader can be found in the Open With option on right clicking the file.

---

### Post by kiemtra on 2012-02-04
This thread was useless for me.

I knew about the "Open with" in the Properties tab.

But what if the application (here, Adobe Acrobat) isn't there?

Here what solved my problem (in Gnome):

Open the file /etc/gnome/defaults.list (admin mode).

Change the line: 
application/pdf=evince.desktop

to:
application/pdf=acroread.desktop

Done.

---

### Post by has64 on 2012-03-26
> **kiemtra said:**
> This thread was useless for me.

I knew about the "Open with" in the Properties tab.

But what if the application (here, Adobe Acrobat) isn't there?

Here what solved my problem (in Gnome):

Open the file /etc/gnome/defaults.list (admin mode).

Change the line: 
application/pdf=evince.desktop

to:
application/pdf=acroread.desktop

Done.
Thanks!, It works for me!

---

### Post by amitava_1952 on 2012-04-18
> **kiemtra said:**
> This thread was useless for me.

I knew about the "Open with" in the Properties tab.

But what if the application (here, Adobe Acrobat) isn't there?

Here what solved my problem (in Gnome):

Open the file /etc/gnome/defaults.list (admin mode).

Change the line: 
application/pdf=evince.desktop

to:
application/pdf=acroread.desktop

Done.
This indeed seems to be the current way to do it. I tried my earlier method after reinstallation, and it did not work.

Thanks

---

### Post by JazzerAtHeart on 2012-06-28
> **kiemtra said:**
> This thread was useless for me.

I knew about the "Open with" in the Properties tab.

But what if the application (here, Adobe Acrobat) isn't there?

Here what solved my problem (in Gnome):

Open the file /etc/gnome/defaults.list (admin mode).

Change the line: 
application/pdf=evince.desktop

to:
application/pdf=acroread.desktop

Done.


This worked great for me as well.
Just had to edit it through cmd line.

```
sudo gedit /etc/gnome/defaults.list

```
Line 7 had it right there.

Thanks. :-)

---

### Post by NikTh on 2012-06-28
If you "hack" the /usr/share/applications ? i am not sure but you can try it. 
Replace evince.desktop with acroread.desktop

---

### Post by ben2mx on 2012-08-21
Worked for me as well. 12.04

> **JazzerAtHeart said:**
> This worked great for me as well.
Just had to edit it through cmd line.

```
sudo gedit /etc/gnome/defaults.list

```Line 7 had it right there.

Thanks. :-)

---

### Post by apollothethird on 2012-09-29
> **ben2mx said:**
> Worked for me as well. 12.04

I find it problematic if you have to change every preference for systemwide users.  I hope someone will provide us with a way to allow a per user default.  Like everyone here so far, I prefer the Adobe program in favor of the Vince program in this case.  However, I had to do the same systemwide to make Opera my default browser.  Some of the people who share my computer would prefer Firefox or Chrome for their default browser.  I can't figure out a way to allow them to have different defaults than me.

Hopefully someone reviewing this thread will shed some light on this.

I also find it problematic that a person would have to be the super user to setup individual preferences with a multiuser OS.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2012-09-29
> **apollothethird said:**
> I find it problematic if you have to change every preference for systemwide users.  I hope someone will provide us with a way to allow a per user default.  Like everyone here so far, I prefer the Adobe program in favor of the Vince program in this case.  However, I had to do the same systemwide to make Opera my default browser.  Some of the people who share my computer would prefer Firefox or Chrome for their default browser.  I can't figure out a way to allow them to have different defaults than me.

Hopefully someone reviewing this thread will shed some light on this.

I also find it problematic that a person would have to be the super user to setup individual preferences with a multiuser OS.


After significant research it turns out that the per user counterpart is:

~/.local/share/applications/mimeapps.list

You can also create a [Named Application].desktop file with a text editor under "~/.local/share/applicatons/" and add a "%f" parameter to the "exec=" option.  This will make the application appear in the available default type list.

I copied the "acroread.desktop" file from /usr/share/applications to "~/.local/share/applications" and added the "%f" then right clicked the PDF file and used the original steps provided in this thread that didn't work before.

new acroread.desktop file:
```

[Desktop Entry]
Name=Adobe Reader 9
MimeType=application/pdf;application/vnd.fdf;application/vnd.adobe.pdx;applicat\
ion/vnd.adobe.xdp+xml;application/vnd.adobe.xfdf;
Exec=acroread %f
Type=Application
GenericName=PDF Viewer
Terminal=false
Icon=AdobeReader9
Caption=PDF Viewer
X-KDE-StartupNotify=false
Categories=Application;Office;Viewer;X-Red-Hat-Base;
InitialPreference=9

```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by fchristiny on 2012-10-11
I am trying to give apollothethird 5 stars for his answer.  How come there is no place to do that in this forum?

---

