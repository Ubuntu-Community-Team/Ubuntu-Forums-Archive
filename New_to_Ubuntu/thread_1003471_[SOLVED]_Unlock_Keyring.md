---
title: "[SOLVED] Unlock Keyring"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by misswham on 2008-12-06
I am getting a message saying

Enter password for default keyring to unlock

The application 'nm-applet' (/usr/bin/nm-applet) wants access tot eh default keying, but it is locked

Password

                               deny   ok

This just happened on my laptop lastnight.  What does this mean?  What is a keyring?

---

### Post by lovinglinux on 2008-12-06
[From Wikipedia]("http://en.wikipedia.org/wiki/GNOME_Keyring")
```
GNOME Keyring is a program designed to take care of the user's security credentials, such as user names and passwords, in an easy to access manner.

The keyring is implemented as a daemon and uses the process name gnome-keyring-daemon.

GNOME Keyring and GNOME Keyring Manager are both part of the GNOME desktop and are entirely developed within the GnomeLive project.
```

So, the keyring is "like" the password manager of Firefox, but for Gnome. It stores encrypted keys, passphrases and plain passwords. For example, it stores the encrypted keys for encrypting/decrypting files in your system, the passwords of those Gmail checkers applets, the public keys of software sources and your wireless encrypted key.

The nm-applet is the network manager. It is trying to access the keyring to retrieve the wireless encryption password, so it can connect automatically without entering the long and meaningless series of characters ever time. So, you need to type the keyring passphrase to unlock it. The keyring passphrase is like Firefox master password, that you need to type to fill log in forms automatically.

If you want to connect automatically, without entering the passphrase every time, you need to save the keyring without a passphrase or make it unlock automatically when you login.

I guess there is a bug in the keyring, because it should unlock it when you login. This also happened in my notebook running Intrepid.

The solution I have found is to recreate the keyring without a passphrase. To do this, open the folder ~/.gnome2/keyrings, then delete the "default.keyring" file (back it up first). Then try to connect to the wireless network. It will ask for the WAP encryption key again (the one configured in your router). Then, when it asks for the passphrase, just click OK without entering one. It will save the keyring unencrypted, so when the machine tries to connect to the wireless network again it won't ask for the passphrase to unlock the keyring.

---

### Post by SamNSane on 2008-12-06
I've always got the network manager to work correctly (no prompt after startup when connecting to wireless) by setting the password for the default keyring to be the same as the login password for the user account.

I just go into the menu system (Accessories | Passwords and Encryption Keys). Once that application opens I go to Edit | Preferences. In the Password Keyrings tab I select "login Automatically unlocked when user logs in." Then I click on the Change Unlock Password button. This brings up a dialog in which you have to type in the old password. (Hint: If you've never been in this location before, that password will probably be the first one you ever used for your account on this system. Of course, if you've changed the keyring password from a terminal window, then all bets are off.) Once you have the login password keyring set to match your normal account login password, this keyring (which should be the default keyring for the network manager to use) should be unlocked every time you log on to the account. In that case you should get no prompt for the keyring password when wireless tries to connect.

It has worked that way for me in both Hardy and Intrepid. The only problem is that you have to remember to go into the Passwords and Encryption Keys application to change the login password keyring every time you change your account password, or the synchronization is broken.

I think this doesn't work well with automatic logins, though I don't know whether that's a bug or just that people get things unsynchronized. I've never checked it out because I'd never use automatic login.

Another way around this, of course, is to change what application does your network management. In Hardy, I use wicd on laptop systems that get moved around from network to network because it's a heck of a lot better at network management than Hardy's version of network manager.

Using wicd, however, has a small security problem in that anyone with access to the unlocked desktop can change basic network settings. Of course I'm as unlikely to leave my unlocked desktop unattended as I am to use automatic login. But this could be a real problem for some multi-user systems.

Intrepid's version of the network manager is much, much better and should work for just about anyone, though it still has this need for synchronization between the keyring password and the account password.

---

### Post by lovinglinux on 2008-12-06
> **SamNSane said:**
> I think this doesn't work well with automatic logins, though I don't know whether that's a bug or just that people get things unsynchronized. I've never checked it out because I'd never use automatic login.

Yep. I forgot to mention that. I'm using automatic login and it doesn't work. Nevertheless, if you are not using automatic login, then your solution is the best way of making the wireless login.

---

### Post by andrewsimpson on 2008-12-14
Having been through this too; I found lots people asking, but few answers.

1. Choose Applications --> Accessories --> Passwords and Encryption Keys.

2. In the application, chose Edit --> Preferences

3. Highlight the 'login' text in the main box, and choose 'Change Unlock Password'.

4. Enter your normal login password for current password.  Leave the new password fields blank (as in "no password").

5. Click 'Change'.  Expect a dialogue box saying that having no passwords is insecure.  Click 'Accept', and keep clicking all the way out!

6. Enjoy your password free Network Manager... :p

Note:  There is another application under System --> Preferences --> Encryption and Keyrings.  This is not what you want - don't try this application ;)

---

### Post by lovinglinux on 2008-12-14
> **andrewsimpson said:**
> Note:  There is another application under System --> Preferences --> Encryption and Keyrings.  This is not what you want - don't try this application ;)

They are both parts of the same tool. You can access the "System --> Preferences --> Encryption and Keyrings" from the preferences menu of "Applications --> Accessories --> Passwords and Encryption Keys". I guess they have different menu entries just to facilitate (or complicate).

---

### Post by SamNSane on 2008-12-14
> **andrewsimpson said:**
> Having been through this too; I found lots people asking, but few answers.

1. Choose Applications --> Accessories --> Passwords and Encryption Keys.

2. In the application, chose Edit --> Preferences

3. Highlight the 'login' text in the main box, and choose 'Change Unlock Password'.

4. Enter your normal login password for current password.  Leave the new password fields blank (as in "no password").

5. Click 'Change'.  Expect a dialogue box saying that having no passwords is insecure.  Click 'Accept', and keep clicking all the way out!

6. Enjoy your password free Network Manager... :p

Note:  There is another application under System --> Preferences --> Encryption and Keyrings.  This is not what you want - don't try this application ;)

You laid it out in a very much nicer format than I did, but that's the same procedure I outlined a couple of posts above yours. Unfortunately, it seems that any alteration at all in the normal scheme of things, logging-in-wise (like using automatic login), seems to discombobulate this feature. And, of course, there are lots of folks who've been through a change of password or two and then run into the problem with needing to set up a new default wireless network. They may no longer have or remember the unlock password they need to use to unlock the manager so they can give it the new password. At this point, direct manipulation of the pertinent file is necessary to fix the issue.

Even though I use wicd to replace Network Manager in HH (because NM in 8.04 is really, really inept for handling lots of different networks, some of which are dhcp and some of which are fixed IP), I continue to go into the Password and Encryption Keys applet to resynchronize the login password after every change of the user account password -- just in case I ever decide / need to revert.

---

### Post by andrewsimpson on 2008-12-14
> **SamNSane said:**
> You laid it out in a very much nicer format than I did, but that's the same procedure I outlined a couple of posts above yours. Unfortunately, it seems that any alteration at all in the normal scheme of things, logging-in-wise (like using automatic login), seems to discombobulate this feature. And, of course, there are lots of folks who've been through a change of password or two and then run into the problem with needing to set up a new default wireless network. They may no longer have or remember the unlock password they need to use to unlock the manager so they can give it the new password. At this point, direct manipulation of the pertinent file is necessary to fix the issue.


The important thing is to set 'no password', then Network Manager can access the keyring without requiring any password.

---

### Post by andrewsimpson on 2008-12-14
> **lovinglinux said:**
> They are both parts of the same tool. You can access the "System --> Preferences --> Encryption and Keyrings" from the preferences menu of "Applications --> Accessories --> Passwords and Encryption Keys". I guess they have different menu entries just to facilitate (or complicate).

Being a long time KDE user (that doesn't like KDE 4.1), you could call me Gnome beginner and usability tester. ):P

There seems to be no (easy) way that you can access the keyring from System --> Preferences --> Encryption and Keyrings.  I spent a long time trying to solve this one, and only found the other route by chance. It was very confusing. :confused:

---

### Post by frankleeee on 2008-12-14
[QUOTE The solution I have found is to recreate the keyring without a passphrase. To do this, open the folder ~/.gnome2/keyrings, then delete the "default.keyring" file (back it up first). Then try to connect to the wireless network. It will ask for the WAP encryption key again (the one configured in your router). Then, when it asks for the passphrase, just click OK without entering one. It will save the keyring unencrypted, so when the machine tries to connect to the wireless network again it won't ask for the passphrase to unlock the keyring.[/QUOTE]

I have used this to reset the keyring but I did not know you could accept the blank and get the auto login to wireless, good info. ;)

---

### Post by lovinglinux on 2008-12-14
> **andrewsimpson said:**
> I spent a long time trying to solve this one, and only found the other route by chance. It was very confusing. :confused:

But that was exactly what I said. You can access the Preferences tool from the Accessories tool, not the inverse.

---

### Post by SamNSane on 2008-12-14
> **andrewsimpson said:**
> The important thing is to set 'no password', then Network Manager can access the keyring without requiring any password.

In which case, I would argue, it doesn't even make sense to keep using Network Manager -- at least certainly not in Hardy. Better of going with wicd, which is more versatile.

---

### Post by frankleeee on 2008-12-14
> **SamNSane said:**
> In which case, I would argue, it doesn't even make sense to keep using Network Manager -- at least certainly not in Hardy. Better of going with wicd, which is more versatile.

I think it is a matter of choice NM-Manager broke in intrepid, so I installed wicd which took a week to go belly up, I reinstalled NM and haven't had a problem since.

---

### Post by andrewsimpson on 2008-12-15
> **lovinglinux said:**
> But that was exactly what I said. You can access the Preferences tool from the Accessories tool, not the inverse.

Apologies, I misread your post.  O.K., I'm getting out of this thread. :-#

---

### Post by SamNSane on 2008-12-15
> **frankleeee said:**
> I think it is a matter of choice NM-Manager broke in intrepid, so I installed wicd which took a week to go belly up, I reinstalled NM and haven't had a problem since.

The nm applet is a LOT better in Intrepid than it is in Hardy. In Hardy, it is just adequate for those who almost exclusively use dhcp to get their IP addresses. It is downright inconvenient-bordering-on-unuseable for people who have to use multiple fixed / dhcp  setups on both wired and wireless networks.

I haven't had either one (nm or wicd) fail on me, no matter how complex the setup I was using. But I can't be bothered to have to go through so much trouble to perform a function that should work darned near automatically, once set up correctly. Wicd has just worked for me in every Ubuntu version I've used. NM, not so much -- until Intrepid.

---

### Post by S_e_P_p on 2008-12-15
Hello all,

just one question. What is about security issues if you set your default keyring password to nothing?

Is there any impact?

Thanks.
Sebastian

---

### Post by SamNSane on 2008-12-15
> **S_e_P_p said:**
> Hello all,

just one question. What is about security issues if you set your default keyring password to nothing?

Is there any impact?

Thanks.
Sebastian

Good question. I'm not sure about it, being a newcomer to the OS. But I make a habit of using strong passwords everywhere they're required. There are a lot of people posting that they're using this tactic of using a blank password, though.

One of the security advantages of the network manager is that making changes to networking settings through it requires entry of an admin password, as it probably should.

I replace network manager with wicd in Hardy installations that have to travel between lots of different networks because the standard Hardy network manager has a really hard time transitioning back-and-forth between dhcp and fixed IP locations. (It's not impossible to do. It's just annoyingly time-consuming and a real bother when you need to get a quick connection.) Wicd does NOT require the use of credentials to acquire access to these basic system settings (networking). That's certainly a security risk, and it would be unacceptable in some circumstances. But I always lock my desktop, log out, or shut down when I leave my systems.

But this leaving a blank password on the gnome-keyring login key access is a different matter than the above concern. I wouldn't do it without doing some research, as you are doing.

There's a security section on these forums. You might have a better chance at getting folks with particular interest in security issues to answer you over there.

---

### Post by andrewsimpson on 2008-12-16
> **S_e_P_p said:**
> 

just one question. What is about security issues if you set your default keyring password to nothing?


It depends on how important security is to you!  For an average user it's probably acceptable.  

Here is the justification.  Firstly, file security:

The keyrings are stored in a file in a hidden directory in your /home directory.  I can list mine like this:

```

$ ls -l  /home/asimpson/.gnome2/keyrings
total 4
-rw------- 1 asimpson asimpson 2072 2008-11-22 12:17 login.keyring

```

The '-rw-------' tells me that asimpson (and no one else except 'root') can read (r) and write (w) to the file login.keyring.

Secondly, the file is in my home directory that only I (and 'root') have access to.

What this means is that regardless of keyring password (or no password), only the user asimpson (or 'root') can access the file and read it. So my stored passwords are safe by virtue of file security.

If someone got access to my user account then they could access my keyring, but personally that's not a big concern to me. I guess also that the 'root' user could access the keyring and cause havoc, but on my system I *am* root too!

If I had some particularly precious passwords, then I'd probably use the password facility on the keyring.  My wireless password is just not that precious to me!

Hopefully all that makes sense.

---

### Post by S_e_P_p on 2008-12-16
> **andrewsimpson said:**
> It depends on how important security is to you!  For an average user it's probably acceptable.  

Here is the justification.  Firstly, file security:

The keyrings are stored in a file in a hidden directory in your /home directory.  I can list mine like this:

```

$ ls -l  /home/asimpson/.gnome2/keyrings
total 4
-rw------- 1 asimpson asimpson 2072 2008-11-22 12:17 login.keyring

```

The '-rw-------' tells me that asimpson (and no one else except 'root') can read (r) and write (w) to the file login.keyring.

Secondly, the file is in my home directory that only I (and 'root') have access to.

What this means is that regardless of keyring password (or no password), only the user asimpson (or 'root') can access the file and read it. So my stored passwords are safe by virtue of file security.

If someone got access to my user account then they could access my keyring, but personally that's not a big concern to me. I guess also that the 'root' user could access the keyring and cause havoc, but on my system I *am* root too!

If I had some particularly precious passwords, then I'd probably use the password facility on the keyring.  My wireless password is just not that precious to me!

Hopefully all that makes sense.

Hello,

Thanks for the information. 

If it's only about the WLAN password it is also not so important for me. It was just afraid that behind this keyring are also other passwords saved which would make it easier for external people to access my computer. If it's not so and only the WLAN keyring is accessible it's no problem at all.

Just one question for understanding the hole keyring story. Would it also be possible to create different keyrings for different passwords ? E.g. WLAN1, WLAN2, EMAIL ...
or these passwords are generally saved under one (GENERAL) Keyring.

This would mean that in the case somebody might access my computer and I set the keyring to 'blank' it's much easier to get "all" my passwords.

Thanks for help.

Sepp

---

### Post by SamNSane on 2008-12-16
I'm watching this conversation and not quite understanding why neither of you is concerned about your WLAN password. If you are using wireless connectivity, and someone else acquires that password they have access to your Internet connection and, possibly, to shares and services on your systems. Even if the shares and services on your systems are really locked down, you might not want to enable someone else to be getting to the Internet from your public IP address for a lot of different reasons.

Now the mere fact that there's no password insofar as access to the keyring goes isn't (afaik) ordinarily a problem so long as other persons aren't give access to your logged on desktop.

However, I would think that malware authors might, if they get the idea that this is common practice among linux users, start writing routines into their software that would make use of the gnome-keyring applet to export users' keyring data, or delete it, or change it. All of those things could happen without your permission when you run their software or their installer, and perhaps without your knowledge. Yes, the keyring file locations themselves wouldn't be available to them directly, but they wouldn't need that. They'd have the gnome-keyring applet to do the work form them. I'm pretty sure that's why it uses passwords.

I would still hope that anyone who is thinking about doing this would take careful stock of their situation and uses for their systems and look assiduously into the security ramifications with folks who are concerned about such things.

I mean absolutely no disrespect to either of you in this matter. Everyone has different ways of doing things, and I'm certain there are many use cases where a lowered security stance is acceptable. But andrewsimpson is stating that he runs as root. This should be a certain indication of a willingness to accept a somewhat more risky (than standard) approach to the use of his system. (Note: The forum management doesn't even allow anyone to post instructions for running a user account as root, even though the process is trivial.) The approach andrewsimpson is taking may work very well, or it may cause him some grief at some point. If his use of his system is such that even total compromise of it is of no concern to him, then there is certainly no downside for him.

In any case, S_e_P_p, I recommend that, since you've expressed some concern about possible security ramifications of using the blank password approach for this applet, you should at least bring the matter up in a security forum or two. It can't hurt to have the advantage of some varied opinions on this matter before you act.

---

### Post by S_e_P_p on 2008-12-16
> **SamNSane said:**
> 
However, I would think that malware authors might, if they get the idea that this is common practice among linux users, start writing routines into their software that would make use of the gnome-keyring applet to export users' keyring data, or delete it, or change it.


Hey SamNSane,

Thanks for you're reply. 

I understand you're point of view and I prefer a secure system. Which means I will put back the default keyring until I have some clarification.

But just some considerations regarding this. What is the advantage they have by accessing your default keyring? The only thing they can access is the WLAN password. As I understood there is only the WLAN password saved, and nothing else. On the other hand the person has to get access to your PC before they are able to access the keyring. 

If they get your WLAN password what to do with it ? They have to find the location of your computer before they are able to access you're wlan. (Based on the Idea the attack it through the internet)

This might be a real big issue for companies but I suppose for private person it is not so serious (On the other hand that is again different from case to case).

This is written on the assumption that only the WLAN password is saved within the default keyring. If somebody could clarify this assumption I would be quite happy.

Thanks.
SePp

---

### Post by Miljet on 2008-12-16
One point that I haven't seen mentioned. I believe that the OP mentioned that this happens on a laptop. On my laptop, during normal startup the keyring is unlocked at login, just as it should be. However, if the laptop is put into hibernation, when it is turned back on it skips the normal login and will ask for the password to unlock the keyring every time.

---

### Post by SamNSane on 2008-12-16
> **S_e_P_p said:**
> Hey SamNSane,

Thanks for you're reply. 

I understand you're point of view and I prefer a secure system. Which means I will put back the default keyring until I have some clarification.

But just some considerations regarding this. What is the advantage they have by accessing your default keyring? The only thing they can access is the WLAN password. As I understood there is only the WLAN password saved, and nothing else. On the other hand the person has to get access to your PC before they are able to access the keyring. 

If they get your WLAN password what to do with it ? They have to find the location of your computer before they are able to access you're wlan. (Based on the Idea the attack it through the internet)

This might be a real big issue for companies but I suppose for private person it is not so serious (On the other hand that is again different from case to case).

This is written on the assumption that only the WLAN password is saved within the default keyring. If somebody could clarify this assumption I would be quite happy.

Thanks.
SePp

If you really want to get detailed information on this, you really should post in another forum. This isn't absolute beginner stuff.

But to give you the simplest case scenarios of which I am aware --

The most common exploits of personal user desktops occur through "social engineering". Someone gets me to click on the wrong link in my browser window or, worse yet, gets me to download software and execute it directly on my system. (We're protected from many browser exploits, but there is a constant string of patches for even Linux browsers for a reason.)

If I am using a blank password for my keyring, then whatever elements of the keyring applet's handling features for the keyrings are exposed through CLI could theoretically be executed by a routine in the malware I just executed. Furthermore, the operating system itself usually makes it possible to supress any outward evidence of the operation in progress, so the malware may export my data, or erase it, or change it without my knowledge.

It is also often possible for malware to be able to make use of readily available application software on the system (mail or chat client, etc.) to send data it has gathered on the system. So, my WLAN key gets sent to someone else, perhaps along with information about the internet-facing IP address of my router, which works out to a pretty darned good idea of exactly where in the world I live, right down to my neighborhood.

Moreover, if I run my user account as root, then anything I execute is run with full root authority, and that is a huge can of worms right there. Assuming I never download and run anything that contains malware, and that I never fall victim to a zero-day exploit of my browser or some part of my operating system or application software, I'll be fine. The odds are probably still with me, unless I'm really dumb enough to be pretty indiscriminate about what I install and run and where I spend my time on the Internet. But those odds are not as good for me as they would be if I kept all of the security features in my system enabled and used strong passwords. If I do that, then I'm going to get prompted with a password request when the malware tries to pull a fast one.

---

### Post by Rayob on 2008-12-16
[Q[CENTER][/CENTER]UOTE=andrewsimpson;6365451]Having been through this too; I found lots people asking, but few answers.

1. Choose Applications --> Accessories --> Passwords and Encryption Keys.

2. In the application, chose Edit --> Preferences

3. Highlight the 'login' text in the main box, and choose 'Change Unlock Password'.

4. Enter your normal login password for current password.  Leave the new password fields blank (as in "no password").

5. Click 'Change'.  Expect a dialogue box saying that having no passwords is insecure.  Click 'Accept', and keep clicking all the way out!

6. Enjoy your password free Network Manager... :p

Note:  There is another application under System --> Preferences --> Encryption and Keyrings.  This is not what you want - don't try this application ;)[/QUOTE]
Thanks, worked a treat

---

### Post by andrewsimpson on 2008-12-16
> Just one question for understanding the hole keyring story. Would it also be possible to create different keyrings for different passwords ? E.g. WLAN1, WLAN2, EMAIL ...
or these passwords are generally saved under one (GENERAL) Keyring.

I think it is indeed possible to have several keyrings with differing passwords.  I haven't tried this....

It's probably a good solution to allow easy access for minor items and sticter access for important items. 

> But andrewsimpson is stating that he runs as root.

I said that the root user and the ordinary user were the same physical person on my system.  Please don't run as root, because that would be foolish (And no, I don't run as root).

> One point that I haven't seen mentioned. I believe that the OP mentioned that this happens on a laptop. On my laptop, during normal startup the keyring is unlocked at login, just as it should be. However, if the laptop is put into hibernation, when it is turned back on it skips the normal login and will ask for the password to unlock the keyring every time.

During an ordinary login the password you enter is passed via a PAM module (gnome-keyring-pam) to the default keyring.  This obviously isn't happening coming out of hibernation.

The same problem occurs with autologin, because PAM can't give an entered password to the keyring.  Remember that passwords in Linux are stored as encrypted so this isn't much use.

This brings us back to the starting point, the only working fix that I know for these two problems is to have 'blank' keyring password.

---

### Post by SamNSane on 2008-12-17
Hmmm. Okay. I wasn't trying to put words in your mouth, but "on my system I *am* root, too" kind of sounded as though you were running as root. Any user account with sufficient privileges is acting (temporarily) as a user with access to root privs for a specific process (and its daughters) when using sudo / gksu, but the account itself (and its user) is still not root. Which is a good thing.

I'm sorry I misrepresented you.

---

### Post by misswham on 2008-12-17
I added a new user last night and when i tried to log on this morning under my username and password, it wouldnt take it and i had to log on under my new username.  Now all of my documents are under the other name and I it wont take my old username or password.  I also tried to make a new thread and for some reason I cant make a new one. I couldnt have been banned because I didnt do anything.  I think its because I cant get to my main username.  Does anyone know what has happened and how can I get back into my main username without wiping my harddrive clean and starting over.

---

### Post by brookie on 2008-12-17
Thanks for all your help. That bugger was annoying me. Cheers, brookie:p

---

### Post by Insomniacno1 on 2010-12-12
> **andrewsimpson said:**
> Having been through this too; I found lots people asking, but few answers.

1. Choose Applications --> Accessories --> Passwords and Encryption Keys.

2. In the application, chose Edit --> Preferences

3. Highlight the 'login' text in the main box, and choose 'Change Unlock Password'.

4. Enter your normal login password for current password.  Leave the new password fields blank (as in "no password").

5. Click 'Change'.  Expect a dialogue box saying that having no passwords is insecure.  Click 'Accept', and keep clicking all the way out!

6. Enjoy your password free Network Manager... :p

Note:  There is another application under System --> Preferences --> Encryption and Keyrings.  This is not what you want - don't try this application ;)


I get the above, but can someone direct me on how to do that when running Peppermint One 08042010 and "Passwords and Encryption Keys" is not present anywhere in the menu?

Thanks in advance

JBJ

---

### Post by Perfect Storm on 2010-12-12
Thread Closed.

Please check the date of the thread.

---

