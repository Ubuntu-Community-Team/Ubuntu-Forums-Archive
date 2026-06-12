---
title: "unlock keyring?"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by amanda hill on 2009-01-08
When I start up my computer it is asking for "password for default keyring to unlock".
The message on the screen says The application 'nm-(/usr/bin/nm-applet) wants access to the default keyring,but it is locked.

I have tried to make a password,but don,t know how to what should I do????

---

### Post by cosine352 on 2009-01-08
It should be your login password.

---

### Post by amanda hill on 2009-01-08
> **cosine352 said:**
> It should be your login password.
that is not working.Prior to this I had a problem with fire fox.which ended with me having to get rid of firefox completely and reinstalling it.I do have a thread on here concerning that.The next 3 times i logged in I was asked for the wep key to access my wireless internet.It still asks for that but now also it asks for this key to unlock as I told you.When I deleted firefox and reinstalled is it possible I deleted all my passwords.If so how do I reset them.

---

### Post by ASchweitzer on 2009-01-08
The message box you're getting is because the application *nm-applet* is trying to access stored passwords in your system (this is independent from firefox, for the record). This application is the Network Manager Applet, which is the little wifi-connection icon in the taskbar. The nm-applet is attempting to use your stored WEP key so it can automagically connect to your network.

Normally, the keyring unlocks itself, when you log in. However, if you've changed your login password at all since your first install, the keyring is still set to the system password you had at the time when the WEP key was first stored. 

Try login passwords that you've had in the past to unlock it.

I've had this issue before, but I can't remember how to get rid of it completely. Try messing around with the "Encryptions and Keyrings" dialog.

---

### Post by ethoxyethaan on 2009-01-08
If you have "auto login" enabled this will pop up,

you entered the password the first time the keyring asked for it so you should know what it is.

---

### Post by marshall.robert on 2009-01-08
I would recommend leaving the password box blank and clicking ok, i did this and now it doesnt ask for my keyring, which is a blessing since i autologin and it used to popup every time i started up.

---

### Post by mister_pink on 2009-01-08
If you go to applications -> Accessories -> Passwords and Encryption Keys, then you can change the password to match your current login password or to be blank if you want.
In the dialog go to Edit -> Preferences, click "login" then "change unlock password"

You'll need to know what the old password is though, which as someone said is probably an old password. Don't really know what to do if you changed the password because you forgot the old one though...

---

### Post by mister_pink on 2009-01-08
If you go to applications -> Accessories -> Passwords and Encryption Keys, then you can change the password to match your current login password or to be blank if you want.
In the dialog go to Edit -> Preferences, click "login" then "change unlock password"

You'll need to know what the old password is though, which as someone said is probably an old password. Don't really know what to do if you changed the password because you forgot the old one though...

---

### Post by stchman on 2009-01-08
The keyring password is the same as your login password by default.  If you changed your login password after you have saved some passwords then you will need to delete those keyrings.

---

### Post by mirhciulica on 2009-01-08
I was having the same problem. The password for the keyring isn't the login password. To reset it you have to delete the default.keyring file from ~/.gnome2/keyrings directory. And then you'll be asked to set a password for keyring ;)
This worked for me. Hope for you too!

---

### Post by amanda hill on 2009-01-08
reply message says :couldn't find package freedom

---

### Post by amanda hill on 2009-01-08
> **mirhciulica said:**
> I was having the same problem. The password for the keyring isn't the login password. To reset it you have to delete the default.keyring file from ~/.gnome2/keyrings directory. And then you'll be asked to set a password for keyring ;)
This worked for me. Hope for you too!
just says .gnome2/keyrings:is a directory?

---

### Post by mirhciulica on 2009-01-09
type this in terminal:
```

cd ~/.gnome2/keyrings
rm default.keyring
```
if default.keyring doesn't exist, try login.keyring instead.

---

### Post by amanda hill on 2009-01-09
> **mirhciulica said:**
> type this in terminal:
```

cd ~/.gnome2/keyrings
rm default.keyring
```
if default.keyring doesn't exist, try login.keyring instead.
cd ~/. gnome2keyring rm default.keyring bash: cd: /home/lily/.gnome2keyrings:No such file or directory. rm login.keyring
rm.cannot remove  'login.keyring': No such file or directory.This is what I got.

---

### Post by mirhciulica on 2009-01-09
> **amanda hill said:**
> cd ~/. gnome2keyring rm default.keyring bash: cd: /home/lily/.gnome2keyrings:No such file or directory. rm login.keyring
rm.cannot remove  'login.keyring': No such file or directory.This is what I got.

[COLOR="DarkRed"]cd ~/. gnome2keyring[/COLOR] you forgot to put / after gnome2
please copy the lines as I wrote to you and paste in terminal ;)
Or you can delete the file by this: open home folder, press Ctrl+H, enter .gnome2 folder and then keyrings, and delete the file from there.

---

### Post by amanda hill on 2009-01-10
the codes are not working.The other option did not work either

---

### Post by mirhciulica on 2009-01-10
Are you sure you use Ubuntu, more specific, with Gnome? Go to panel, Accessories, passwords and encryption keys. click edit in menu, preferences. Select the keyring from list and click on remove keyring.

---

### Post by amanda hill on 2009-01-10
there are no keyrings listed.

---

### Post by dynathi on 2009-01-10
I've managed to reproduce this on my desktop computer. Here's how I got around it:
(I based this off the information in the posts by marshall.robert and mirhciulica, thanks guys)

Under the Applications menu, go to **Accessories** and click on "**Passwords and Encryption Keys**".

Click on **Edit**, and then **Preferences**. A new window will appear. In the box that says "Password Keyrings", there should be an entry called "**default**." Click on it, and then click on "**Remove Keyring**." It will ask you if you are sure, so click on "**Delete**."

Now you can close all your windows. Restart your computer (a Dell Mini 9 if I remember correctly?). It will ask you for the encryption key for your network, so enter it here (this is the "password" for your network, the one you enter on all your computers). 

Now, here's the important part:
It should ask you to choose a password for default keyring.
**Do not enter in a password.** Leave the fields blank. If you do enter in a passsword, it will keep on asking you for it.

Click on **Create**, and it will warn you that you are storing your passwords unencrypted. Click on "**Use Unsafe Storage**."

You should be in! Now, everytime you start up, it should just connect automatically without asking for a password. Hope this helped :) If you have any trouble with these steps, just ask.

**Note:** Someone will probably point out that storing your passwords unencrypted might not be a good idea. And they'd be right, mostly. If you're worried about someone physically stealing your computer and finding out the password to your wireless network, well, just ask and we can walk you through setting up a password. But that'd just get you to where you were in the first place.

---

### Post by amanda hill on 2009-01-10
Ok I have managed to get through this unlock default key problem thankyou,however now the computer asks me for my WEP key Every time I log in .How do I get it to automatically login??????????.Do you think any of this is related to my earlier firefox problem? just wondering

---

### Post by dynathi on 2009-01-11
> **amanda hill said:**
> the computer asks me for my WEP key Every time I log in .How do I get it to automatically login??????????.Do you think any of this is related to my earlier firefox problem? just wondering

Hmm... I think it's probably not related to your firefox problem.

I was doing some searching on the internet, and it seems that a lot of people were having the same problem as you. Unfortunately I couldn't find any solutions, and I wasn't able to reproduce this problem on my computer (it seems to save the password alright), but we could try the following:

-Right click on network icon in the top right, (it might look like five ascending bars). Click on edit connections, and click on the wireless tab. Click on the entry in the list that has the name of your network, and then click on delete, and delete again in the confirmation window that pops up. Close that window.
- Go through the steps I posted before about deleting keys, up to restarting the computer. After you restart your computer connect to the network again by clicking on the network icon and selecting your network from the dropdown list. Then follow through with the rest of the steps.

If this doesn't work, you could try posting a question to the dell mini launchpad site [(click here, you will need to create a login if you haven't done so already)]("https://answers.launchpad.net/dell-mini/+addquestion/"), or maybe someone else can help you here. Sorry, I can't really help you too much because I can't reproduce the problem :(

---

### Post by amanda hill on 2009-01-11
thanks for your help.incidently I have 2 of these computers mini inpiron 9 the one that is functioning fine lists "passphrase for wireless network amandahill" under the passwords section.the one that is not automatically logging in does not have anything listed under passwords.So there,s my issue I think.but I cannot seem to work out how to add this passphrase that I need.I,m hopeful someone can help me with this.

---

### Post by deodatus on 2009-11-23
This seemed to work for me:

right click on network applet,  select wireless tab,  select the desired wireless connection,  click on edit,  check the box at the bottom that says available to all users,  click on apply,  reboot to test.

I am running Linux Mint 7

---

### Post by F W Adams on 2010-07-29
The post above mine by deodatus seems to be a much better solution as it doesn't involve leaving unencrypted passwords lying around. I achieved the same thing under 10.04 by right clicking the wireless icon then selecting "Edit Connections".

---

### Post by jarviser on 2010-07-30
> **amanda hill said:**
> thanks for your help.incidently I have 2 of these computers mini inpiron 9 the one that is functioning fine lists "passphrase for wireless network amandahill" under the passwords section.the one that is not automatically logging in does not have anything listed under passwords.So there,s my issue I think.but I cannot seem to work out how to add this passphrase that I need.I,m hopeful someone can help me with this.

"Passphrase" is WPA not WEP. The connection probably thinks it is one, but the router is set to the other. Or maybe there is another connection set to auto.
The usual solution for this is the same as in Windows - i.e. delete all the wireless connections and start again, ensuring you tick the box to connect automatically if there is one.
Right Click on the connect icon in the notification area and click Edit Connections
Go to the Wireless Tab and delete the offending connection (or preferably all of them)
Close and then try to connect to wifi again. It should ask for the key or passphrase and it will know that it is either WEP or WPA and will probably ask if you want to connect automatically.

---

