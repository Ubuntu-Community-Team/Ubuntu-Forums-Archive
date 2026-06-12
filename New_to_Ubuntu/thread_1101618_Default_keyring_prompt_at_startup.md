---
title: "Default keyring prompt at startup"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-03-20
Last query of the day...  ;)

When I log in and immediately when the Desktop shows, I get the following message prompt (Ubuntu 8.10):
[B]
Enter Password for default keyring to unlock[/B]
*The application "Network manager Applet" (/urs/bin/nm-applet) wants access to the default keyring, but i*s locked

On a probably related note, I have a cabled ethernet connection to my wireless router but also have a wireless connection - every time I log in I've to untick the "enable wireless" button, as soon as I log out this seems to reset.

---

### Post by lovinglinux on 2009-03-20
Are you using automatic login or do you have to input your username and password before getting to the desktop?

This problem is usually related to automatic login. 

I have the same problem on a notebook running 8.10 here. Unfortunately, I couldn't get rid of the keyring alert, even after using several methods suggested on other threads. Disabling automatic login is not an option in my case, but maybe is for you.

---

### Post by aquascrotum on 2009-03-20
I am using automatic log in (though for some reason it has only worked intermittently so far) - will try disabling it.

---

### Post by openess on 2009-03-21
I have the same problem, but I'm not using automatic login.

I did not have this problem until recently, when I changed my login password. I have to enter my old password everytime I want to conect to the internet, I havn't even found a way to change the password for my default keyring..

---

### Post by aquascrotum on 2009-03-21
well disabling automatic login meant the prompts went away. Does this constitute a bug worth reporting?

---

### Post by blastus on 2009-03-21
Goto Network Connections either by:
1. Right-clicking on the network applet and selecting "Edit Connections"
2. or selecting System -> Preferences -> Network Configuration

The network manager may request access to your keyring upon login if you have modified or added network connections. In my case I had once tried to connect to a wireless network and couldn't but it configured it in network connections anyway and every time I logged in it would request access to the keyring and try to connect to the wireless network. 

Deleting the wireless connection in network manager solved the problem.

---

### Post by lunatico on 2009-03-21
This is happening because when Network Manager is about to use your saved password to authenticate to your network it first needs your permission (to make sure it's you...)
To get rid ("fix") of this:
Go to Applications -> Accessories ->  Passwords and Encryption Keys
Click Edit -> Preferences
Select the line that says:

```
login Automatically unlocked when user logs in.
```

Click Change Unlock Password, type in your Old password and leave fields for new password empty. That's it!

Don't worry, you are not changing your password really, you are just... let's say, lowering security. Something like turning those stupid messages that ask for your permission to do anything on Vista off....

---

### Post by openess on 2009-03-21
> **aquascrotum said:**
> well disabling automatic login meant the prompts went away. Does this constitute a bug worth reporting?

I'm not using automatic login and still have the problem.

and I still wan't to keep my settings for the networks I'm using, there are a few of them and I wouldn't want to connect to everyone "for the first time" every time, especialy the one in school was a ******* to set up :/

---

### Post by lunatico on 2009-03-21
> **openess said:**
> I'm not using automatic login and still have the problem.

Automatic login has nothing to do with this. See my previous post for the fix.

---

### Post by openess on 2009-03-21
thanx for the help lunatico, sound like a good temporary solution, but I'm not that hapy about lowering secutity, feels strange..

What security am I lowering, and I don't really understand vista references.. Never used it ;)

sorry btw for posting on top of your post last time, I'm a slow writer.

---

### Post by lunatico on 2009-03-21
> **openess said:**
> sound like a good temporary solution, but I'm not that hapy about lowering secutity, feels strange.

I think you are safe...

> **openess said:**
> What security am I lowering, 

Basically the keyring stores your passwords for applications, websites and stuff... so you are lowering your security once you are logged in. I mean, don't leave your computer unlocked because with this approach anyone can see your stored passwords. But as I said, once you are logged in with your user. You still have the whole Linux OS security on top to keep you safe. Makes sense?

> **openess said:**
>  and I don't really understand vista references.. Never used it 

Good man! Stay like that, you are not missing on anything.

---

### Post by openess on 2009-03-21
> **lunatico said:**
> 
Basically the keyring stores your passwords for applications, websites and stuff...

I never save passwords for applications or websites, and very little stuff (only my Wlan passwords), so I think I can live with that.

Thanx for a lot of help

---

### Post by Gray Beard on 2009-03-21
I stumbled across a relevant procedure at Dave's Tech Blog Archive under "How to Remove Ubuntu's Password Keyring" (although you actually don't remove anything but the existing login.keyring file). I make no guarantees but it worked for me on my 64-bit Intrepid box. The only difference was in the dialog that appeared after I'd removed the login.keyring file, rebooted and then logged in to my wireless network.
I already had the system set to connect automatically and when it did, it asked me for the WLAN password. After entering that, a dialog popped up and stated that the Keyring wanted to save the WLAN password and I was given three choices...
1. Deny.
2. Allow Once.
3. Always Allow.
I selected Always Allow and then rebooted. The system automatically connected to my WLAN with no questions asked (which is the way it's been working all along on my 32-bit Intrepid box).
I can also tell you that the login.keyring file was replaced but since I don't know what application opens it (if any), I could't tell you what's in it.

---

### Post by anewguy on 2009-03-21
The keyring password will prompted for also whenever the username/password you use to login is different from that stored on the keyring.  In the case of a password change, that only affected your login, but did not change the password on the keyring.  The easiest thing to do and not compromise any security concerns is to simply delete the keyring file.  The next time you boot you will be prompted again for the username password by the keyring - enter in your login username and password and it will stop asking.

Dave :)

---

### Post by openess on 2009-03-22
changed my default keyring password to match my login password, worked a charm :)

No deleted files and no lowered security (I you can call using the same password for everything security ;) )

---

### Post by romuald_geo on 2009-03-23
I've had similar situation.I was loginnig automatically and it always asked me to enter keyring password to connect to wireless network.I followed the steps lunatico suggested and it solved it.Thank you very much! Finally I've managed to get rid of this annoying prompt:)

---

### Post by hovzio on 2009-03-23
> **anewguy said:**
> The keyring password will prompted for also whenever the username/password you use to login is different from that stored on the keyring.  In the case of a password change, that only affected your login, but did not change the password on the keyring.  The easiest thing to do and not compromise any security concerns is to simply delete the keyring file.  The next time you boot you will be prompted again for the username password by the keyring - enter in your login username and password and it will stop asking.

Dave :)

Cool, I've been wondering about this for a quite a while. (Keyring issues after changing the system password) Where is this "keyring file" located. Would love to get this fixed! Thank you:D:D

---

### Post by herend on 2009-03-25
thanks guys for your help.

my keyring problem was solved. :)
(notebook+wifi, clean ubuntu 8.10 install, every user were asked to give password to keyring when notebook want to use a wifi connection)

It's funny that deleting keyring file and advice of lunatico are the same thing.
When you delete ~/.gome2/keyrings/login.keyrings, it resets your keyring password, you will be prompted next time to give a new one (for example empty password is the best)

But you can reset/change your keyring password at Applications/Accessories/password&keyrings, as lunatico described it.

Thanks again,
Steve

---

### Post by dchen37 on 2009-05-03
> **lunatico said:**
> This is happening because when Network Manager is about to use your saved password to authenticate to your network it first needs your permission (to make sure it's you...)
To get rid ("fix") of this:
Go to Applications -> Accessories ->  Passwords and Encryption Keys
Click Edit -> Preferences
Select the line that says:

```
login Automatically unlocked when user logs in.
```

Click Change Unlock Password, type in your Old password and leave fields for new password empty. That's it!

Don't worry, you are not changing your password really, you are just... let's say, lowering security. Something like turning those stupid messages that ask for your permission to do anything on Vista off....

Anyone figure out how to do this under Jaunty?  It seems like they changed the preferences menu.

---

### Post by jaredA on 2009-06-18
Here is how I resolved the keyring prompt (The EASIEST and the SAFEST, security wise, way):

System: Ubuntu 8.04
Login Type: Auto Login

1 - Go to System >> Administration >> Users and Groups
2 - Click on "Unlock"
3 - Highlight the User account you are having the "keyring issue" with >> Click "Properties"
4 - Click on the tab "User Privileges"
5 - Check the box "Connect to wireless and ethernet networks" >> click "OK"
6 - Restart.

Hope this helps.

---

### Post by wolterh on 2009-06-20
Same problem here, dchen. Lunatico, where are you?? :S

---

### Post by zeezam on 2009-12-28
> **lunatico said:**
> This is happening because when Network Manager is about to use your saved password to authenticate to your network it first needs your permission (to make sure it's you...)
To get rid ("fix") of this:
Go to Applications -> Accessories ->  Passwords and Encryption Keys
Click Edit -> Preferences
Select the line that says:

```
login Automatically unlocked when user logs in.
```

Click Change Unlock Password, type in your Old password and leave fields for new password empty. That's it!

Don't worry, you are not changing your password really, you are just... let's say, lowering security. Something like turning those stupid messages that ask for your permission to do anything on Vista off....

I don't have that option. I'm using karmic.

> **jaredA said:**
> Here is how I resolved the keyring prompt (The EASIEST and the SAFEST, security wise, way):

System: Ubuntu 8.04
Login Type: Auto Login

1 - Go to System >> Administration >> Users and Groups
2 - Click on "Unlock"
3 - Highlight the User account you are having the "keyring issue" with >> Click "Properties"
4 - Click on the tab "User Privileges"
5 - Check the box "Connect to wireless and ethernet networks" >> click "OK"
6 - Restart.

Hope this helps.

Karmic & autologin.
Autoconnect to wifi but have to enter keyring pass everytime...
So your solution didn't work for me. :(

---

### Post by sahoo on 2010-06-03
> **lunatico said:**
> Automatic login has nothing to do with this. See my previous post for the fix.

I don't know all the technicalities to have a concrete opinion. I just faced the same problem and disabling automatic login seems to have fixed the issue.

---

### Post by Heering80 on 2011-01-30
Hi all..

I had the same problem. It was caused by the IM status plugin in rythmbox. Just disable it.

---

