---
title: "Openoffice.org3 is missing the Start Center"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Dj Melik on 2008-12-02
I updated to Openoffice.org3 earlier and now I'm missing the start center :/ I tried everything to re-enable but I can't seem to do so.

[img]http://blogs.computerworld.com/sites/default/themes/cw_blogs/cache/files/u98/Start_Centre.jpg[/img]

This is a picture of the start center I'm talking about. Whenever I open OOo, that doesn't show up. Not a very big problem, but its just annoying me; anyway I can fix this?

---

### Post by Silare Alvreon VI on 2008-12-02
You have two choices:

01.) Alt+F2 and type "openoffice.org3" and it'll start up that way.

02.) Make a new Launcher (be it in your menu or on your panel) for that command.

That should bring your Start Centre back.

---

### Post by gshockxc on 2008-12-02
> **Dj Melik said:**
> I updated to Openoffice.org3 earlier and now I'm missing the start center 

How did you update to OOo3?  I can only seem to find 2.4.

---

### Post by Dj Melik on 2008-12-02
Download the .deb file from [http://openoffice.org](http://openoffice.org)

---

### Post by R2D2! on 2008-12-02
> **gshockxc said:**
> How did you update to OOo3?  I can only seem to find 2.4.

You have to download &#305;t from [www.openoffice.org](www.openoffice.org), as far as I know

—Ilhu&#305;temoc &#948;

---

### Post by gshockxc on 2008-12-02
> **R2D2! said:**
> You have to download &#305;t from [www.openoffice.org](www.openoffice.org), as far as I know

—Ilhu&#305;temoc &#948;

I should know, but I haven't had time to read the documentation... how do you install it?

---

### Post by Dj Melik on 2008-12-02
You just open it and click install. Deb files are very easy to install.

[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0)

---

### Post by Silare Alvreon VI on 2008-12-02
It'll give you a giant archive. Extract it somewhere, and then if you want to install it quickly without double-clicking on a bajillion .deb packages, then you can use Terminal to save yourself some trouble.

01.) Press [Alt+F2] and type gksu gnome-terminal - this will request your password since it's opening the Terminal under a root account.

02.) Go to the DEBS directory whereever it may be (you can see what's in the folder you're in by typing "ls" and navigate to a folder by typing "cd NAME-OF-FOLDER" to change directory to there.

EX: For instance, I put my DEBS directory under /home/silare/Downloads/DEBS - I could type cd /home/silare/Downloads/DEBS

03.) Now, assuming you're in root... Type the following command:

dpkg -i *

It should install every package in your DEBS directory. However, there is a folder called desktop-integration as well. If you want to put OpenOffice.org 3 launchers in your menu like OpenOffice.org 2 did, as well as wipe away all of OpenOffice.org 2 (and don't mind wiping desktop-core away with it too) at the same time, then you can also type the following commands:

cd desktop-integration
dpkg -i *

This puts you in the desktop-integration folder and then lets you install that last package.

Hope this saves some time for you.

---

### Post by gshockxc on 2008-12-02
> **Silare Alvreon VI said:**
> 
02.) Go to the DEBS directory whereever it may be (you can see what's in the folder you're in by typing "ls" and navigate to a folder by typing "cd NAME-OF-FOLDER" to change directory to there.

I think I'm making some progress with this, and yes it is saving me time.  Thanks.  Just because I'm a Noob, and don't know any better yet, I extracted it on the Desktop.  But when I try and run the commands you gave me, it doesn't let me do the dpkg -i*  If I type dpkg --help, I see the command listed there.  

So here's where I'm at: root@gshockxc:/home/gshockxc/Desktop#  I'm guessing this won't work.... because it hasn't so far.  ;/

I took a screen shot of what I'm seeing.  Let me know where I'm going wrong.  Also, I created the same file structure as you to duplicate what you suggested.  Not sure if I did it correctly.  Let me know.  

Thanks for the help.

---

### Post by Beernut on 2008-12-02
If you open a blank calc, writer document close the document not Openoffice and the Start Center will be underneath.

[IMG]http://www.advbuildllc.com/screenshots/Start%20center.png[/IMG]

---

### Post by Silare Alvreon VI on 2008-12-02
Actually, you typed the following:

dpkg --install

That actually is the correct command. However, you pretty much said "Debian Package Manager, I want you to install this." You left out the asterisk. >_> Since it's on your desktop (thus meaning that things like launchers or shortcuts will also be on it), try this:

dpkg --install *.deb

(( P.S. In the case of the dpkg -i * command, don't forget the space between the -i and the *. ))

---

### Post by gshockxc on 2008-12-02
> **Silare Alvreon VI said:**
> (( P.S. In the case of the dpkg -i * command, don't forget the space between the -i and the *. ))

BINGO!!!  In addition to that, when I extracted the files, the folder had the same name as the tar.gs file.  The DEBS folder was inside of that.  So I renamed the folder, and navigated to the DEBS folder - intact, as you indicated it would be.  Then I ran the dpkg -i * command, and it worked like a charm. 

Unfortunately, the desktop-integration isn't going as well.  I'm getting the following error: Conflicts with the installed package 'openoffice.org-core'

Any ideas?  Thanks for all of your help so far.  Half of the problem is just knowing what you mean.  That's just my learning curve.  I really appreciate the help.

---

### Post by gshockxc on 2008-12-02
I started a new thread.  I shouldn't have hijacked this one.  Sorry.

---

