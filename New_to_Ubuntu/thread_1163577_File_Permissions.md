---
title: "File Permissions"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by lile001 on 2009-05-18
I can't really do much on my new Ubuntu system, because apparently I don't have permissions to change anything or save any files.  This of course doesn't make sense because of these things:

1.  When I set up the system, I gave myself administratiive rights at install.
2. I've gone through these steps (straight outta the help file:)

"Giving administrative access to a user
    * Administrative Tasks
You can restrict and enable administrative access (sudo) to users with the Users and Groups application:
   1.Click System &#9656; Administration &#9656; Users and Groups
                        
   2.Click Unlock and enter your password
                      
   3.Select the user who is to be given administrative access and press Properties
                          
   4. Select the User Privileges tab
                          
   5.Check the box next to Administer the system and press OK"

When I do this, no matter whether I check everything or uncheck everything, I still don't have permission to write anything to any files.  Especially my video card configuration, which means my video doesn't work right.  But htat's another thread. 

Now, when I go to the Users and Groups screen,  I notice that ROOT doesn't have permission to do anything!  All boxes are unchecked.  I'm not making much sense of this, I thought Root could do anything?

Not that I really understand what the heck root is, yet, anyway.  

Can anyone help me make some sense of this?

---

### Post by michy99 on 2009-05-18
Many configuration files can only be written to by root. This is as it should be. To edit such files, you can open a terminal and enter```
gksudo gedit {name-of-file}
```Where {name-of-file} is the file you want to edit.

This will open a text editor with root privileges. Use carefully.

---

### Post by pastalavista on 2009-05-18
to  just generally change permissions of drives and things that aren't system critical use : ```
gksu nautilus
``` which will open a 'root' browser. You can then right click any file or folder and select properties and open the permissions tab and set the perissions exactly to your preferences without a lot of terminal code. Be careful in the root browser though unless you know what you're doing. Sudo gives you root priveleges in command line, gksu does the same in GUI applications.

---

### Post by SunnyRabbiera on 2009-05-18
a good way to remedy this is to install nautilus-gksu, it will be able to get around needing the terminal for administration access.

---

### Post by lile001 on 2009-05-18
> **michy99 said:**
> Many configuration files can only be written to by root. This is as it should be. To edit such files, you can open a terminal and enter```
gksudo gedit {name-of-file}
```Where {name-of-file} is the file you want to edit.

This will open a text editor with root privileges. Use carefully.

Hmm..  I'm still not getting this.  I'm in a window called NVIDIA X server settings, and it wants to save a file called /etc/x11/xorg.conf, but I don't have permissions to save that file.  How does a text editor help this?

---

### Post by lile001 on 2009-05-18
> **pastalavista said:**
> to  just generally change permissions of drives and things that aren't system critical use : ```
gksu nautilus
``` which will open a 'root' browser. You can then right click any file or folder and select properties and open the permissions tab and set the perissions exactly to your preferences without a lot of terminal code. Be careful in the root browser though unless you know what you're doing. Sudo gives you root priveleges in command line, gksu does the same in GUI applications.

"Be careful in the root browser though unless you know what you're doing." 

Of course... I don't know what I am doing!  I'll try this and see if I can wreck my computer again.  So what if I have to format and reinstall again?  I've only done it 5X now.  

I'll try to give myself permission to write in the /etc directory  That seems harmless enough (ulp!)   [clack clack clack]

Well, that was no problem.  Heres the result:

      "Failed to run nautilus as user root.

        The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

at least nothing is wrecked. I wish i knew who the system administrator is.  Wait! That's me!

---

### Post by lile001 on 2009-05-18
> **SunnyRabbiera said:**
> a good way to remedy this is to install nautilus-gksu, it will be able to get around needing the terminal for administration access.


I'm really reluctant to add more programs to a system that I don't know how to run right out of the box.  This doesn't sound like a great idea for me.  Maybe I need to understand the basics first before adding fancy stuff.

---

### Post by lile001 on 2009-05-18
> **michy99 said:**
> Many configuration files can only be written to by root. This is as it should be. To edit such files, you can open a terminal and enter```
gksudo gedit {name-of-file}
```Where {name-of-file} is the file you want to edit.

This will open a text editor with root privileges. Use carefully.

If I try anything with Sudo (remember, i have no idea what I am doing - might as well pick up a loaded gun) it says that larry is not in the Sodoers file, and "this incident will be reported".  Looks like no Christmas presents for larry this year after they tell Santa about this.  

There's something real basic missing here.

---

### Post by taurus on 2009-05-18
Are you the original user that you created when you installed Ubuntu?

What's the output of this command from a terminal?  You need to belong to group admin if you want to edit anything outside of your own $HOME.

```
id
```

---

### Post by lile001 on 2009-05-18
> **taurus said:**
> Are you the original user that you created when you installed Ubuntu?

Well, I think so.....

What's the output of this command from a terminal?  You need to belong to group admin if you want to edit anything outside of your own $HOME.

```
id
```

uid=1000(larry) gid-1000(larry) groups=1000(larry).  What does that gibberish mean?

---

### Post by amingv on 2009-05-18
> **lile001 said:**
> Hmm..  I'm still not getting this.  I'm in a window called NVIDIA X server settings, and it wants to save a file called /etc/x11/xorg.conf, but I don't have permissions to save that file.  How does a text editor help this?

Press ALT+F2

type this:

```
gksudo nvidia-settings
```

Type your login password in the pop-up window that appears, and you should be able to save your changes.

If you want, you can edit the menu and add gksudo in front of the command for the nvidia configuration tool, so you can open it directly later.

---

### Post by taurus on 2009-05-18
> **lile001 said:**
> uid=1000(larry) gid-1000(larry) groups=1000(larry).  What does that gibberish mean?

It means you don't have permission to use sudo/gksudo (can't modify system) since you don't belong to group admin.  Did you somehow manager to remove yourself from group admin?

---

### Post by oldos2er on 2009-05-18
> **lile001 said:**
> Hmm..  I'm still not getting this.  I'm in a window called NVIDIA X server settings, and it wants to save a file called /etc/x11/xorg.conf, but I don't have permissions to save that file.  How does a text editor help this?

 In a terminal, run "gksu nvidia-settings".

---

### Post by lile001 on 2009-05-18
> **taurus said:**
> It means you don't have permission to use sudo/gksudo (can't modify system) since you don't belong to group admin.  Did you somehow manager to remove yourself from group admin?


Ah - this seems to explain things more than the other two answers, which seem to tell me to do the same things that didn't work before.  I don't have any idea how to put someone in or take them out of group Admin.  I ran Ubuntu install, answered some questions, and kablam! Next thing I try to do is set up my video and I'm locked out.  And confused. 

 So there was some crucial step missed in the install process?  Do i go back to bare metal again (hey - 6 times is a charm, right?)  

Is there something special about the numero Uno first username you put in the system?

---

### Post by lile001 on 2009-05-18
> **oldos2er said:**
> In a terminal, run "gksu nvidia-settings".
Yeah, i'm still not an admin so this doesn't work.  Is there something about the NVIDEA window that would have told me that the filename "nvidea-settings" was the correct one?  I kept looking to try to see what file it was, but couldn't find anything through the graphical interface.  Or do you just know this somehow?

---

### Post by amingv on 2009-05-18
> **taurus said:**
> It means you don't have permission to use sudo/gksudo (can't modify system) since you don't belong to group admin.  Did you somehow manager to remove yourself from group admin?

Are you really on that group alone? Did you add this user later on or when you installed?

You need to add yourself to the admin group before trying my first sugestion.

If you set this user later on after installation, log in with your primary user and type this on a terminal:

```
for i in adm dialout cdrom plugdev lpadmin admin; do sudo usermod -aG $i <username_of_the_other_account_here>; done

```

If you don't have another user, and somehow this one messed up, reboot in single user mode (follow the steps [here]("http://www.psychocats.net/ubuntu/resetpassword") up until you drop to root shell) and then type:

```
for i in  adm dialout cdrom plugdev lpadmin admin; do usermod -aG $i <username_of_the_other_account_here>; done
```

Make sure you put the broken username where it says "<username_of_the_other_account_here>" and that you type the command correctly.

EDIT:
I threw in some other groups you might like to be added to, but the main one you're looking for is admin.

---

### Post by taurus on 2009-05-18
The user that you created during the installing process should have a UID of 1000 and that user would be automatically added to group admin so he/she can modify system files.  Otherwise, how would he/she run the sudo apt-get update && sudo apt-get upgrade to upgrade the system?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And if you are the original user but somehow got locked out of your system (can't use sudo/gksudo), it means you have done something to your account that managed to remove admin from your group.  Therefore, you need to boot into recovery mode from GRUB menu and add yourself, larry, back to group admin before you can use sudo/gksudo again.

```
useradd -G admin larry
id larry
```

---

### Post by oldos2er on 2009-05-18
The first user you create on installation is given administrative (or root) privileges; once installation is complete you shouldn't need to change these privileges. If you've somehow removed or changed them you may be looking at a reinstall. Someone more experienced than I will need to advise you.

---

### Post by lile001 on 2009-05-18
> **oldos2er said:**
> The first user you create on installation is given administrative (or root) privileges; once installation is complete you shouldn't need to change these privileges. If you've somehow removed or changed them you may be looking at a reinstall. Someone more experienced than I will need to advise you.


Oh.  Oh my.    



The first user created did NOT have administrative priveleges, but the second one was supposed to.  So in effect niether one of them does, which means everybody is locked out. Right?   It looks like I am typing on, in that case, an elaborate boat-anchor.  Only thing it lacks is a chain to lower it over the gunnel into the briny deep.  

Windows XP Install, I believe, can reformat the hard drive without no stinking permissions!  It's a dual boot system anyway.  Back to bare metal!

---

### Post by SunnyRabbiera on 2009-05-18
> **lile001 said:**
> Windows XP Install, I believe, can reformat the hard drive without no stinking permissions!  It's a dual boot system anyway.  Back to bare metal!

Look the reason why we have administrative passwords here on Ubuntu is for security.
Wonder why there are so many viruses and junkware on Windows?
Because the default user is the administrator, windows by default gives the main user full access to the system yes but at great compromise to security.
Like I said you could have saved yourself a lot of tourble by installikg gksu-nautilus.
It will allow you to enter the more sensitive parts of your system without the need of a terminal or anything.
It helps, trust me I would not tell someone to use something I do not trust.
It wont harm your system if you use it properly.

---

### Post by lile001 on 2009-05-18
> **SunnyRabbiera said:**
> Look the reason why we have administrative passwords here on Ubuntu is for security.
Wonder why there are so many viruses and junkware on Windows?
Because the default user is the administrator, windows by default gives the main user full access to the system yes but at great compromise to security.
Like I said you could have saved yourself a lot of tourble by installikg gksu-nautilus.
It will allow you to enter the more sensitive parts of your system without the need of a terminal or anything.
It helps, trust me I would not tell someone to use something I do not trust.
It wont harm your system if you use it properly.

Thanks for the advice, however it doesn't get to the heart of the problem.  I can't do *anything* on this system, including taking your excellent and well-thought-out advice, because of an innocent mistake during install, the kinda bonehead blunder that n00bs often make, because there isn't any hint that this was important.   Yes, I'm quite aware of the problems with Windoze, that's why I'm here blundering around in the dark trying to learn Linux.  I'm also doomed to make every stupid mistake possible along the way.  Oh well.  Where's that install disk?

---

