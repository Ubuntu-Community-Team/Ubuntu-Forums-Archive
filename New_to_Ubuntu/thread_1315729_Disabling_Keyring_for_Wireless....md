---
title: "Disabling Keyring for Wireless..."
date: 2009-11-05
forum: New to Ubuntu
---

### Post by pablolie on 2009-11-05
i have done a search and see that there are several messages about this, but under 9.10 nothing seems to work to disable to password check for wireless (yes, with auto-logon enabled). 

i want it all to turn on automatically - let me worry about the degree of security i want or need. this is an open computer for simple web browsing, no one stores passwords or important information on it, so i just want it to turn on and *work*.

so how does go about it? i have tried pretty much everything under apps- accessories- passwords and encryption keys. but this is one stubborn little piece of software. i do see that one could turn off the "gnome keyring" service or so, but i am afraid of breaking something else.

any input appreciated. i truly think the keyring thing is a bit of an annoyance in Ubuntu out of the box. those who want security would not configure an open account, those who do don't want to enter keyrings - it defeats the purpose of auto-login entirely.

would it go away by installing wicd?

---

### Post by snkiz on 2009-11-05
Try using network manager to set the network in question to available to all users. That will take your key away from gnome-keyring and set it in a system file that root owns. That being said gnome-keyring will not unlock  automatically with auto-login by design. Anything else thats in there will still be locked until some program asks for a password, then the keyring will prompt you.

---

### Post by pablolie on 2009-11-05
> **snkiz said:**
> Try using network manager to set the network in question to available to all users. That will take your key away from gnome-keyring and set it in a system file that root owns. That being said gnome-keyring will not unlock  automatically with auto-login by design. Anything else thats in there will still be locked until some program asks for a password, then the keyring will prompt you.

i did set it available to all users. that is why i am puzzled by the stubborn system behavior, but yes, i have auto-login.

i think it does not make *any* sense to have keyrings for users that on purpose unlock their login. it means they *WANT* all functionality to be accessible right away, and no, they don't want to tell everybody what the system password is...

---

### Post by garvinrick4 on 2009-11-30
1. Open up your Home Folder by clicking Places>Home Folder
   2. Press CTRL-H (or click View>Show Hidden Files)
   3. Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
   4. In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.
   5. Delete any files you find within the keyrings folder
   6. Restart the computer

After you restart and login (if you’re automatically logging in) you’ll probably be asked to enter your wireless networks WPA/WEP encryption key.  After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password and lock it away with a new keyring password.  The box looks like this:

Instead of typing in a new password, leave both boxes completely empty and click Create.

You’ll then be asked if you know what the hell you’re doing:

Go ahead and click Use Unsafe Storage.

WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT and not in an encrypted form.  So it is imperative that you are certain no untrustworthy persons can access your user account (either physically or by remote) or they will be able to easily open and read this file and obtain many passwords (for things such as FTP accounts, SSH, e-mail accounts, etc).  Proceed with caution.

From here on all keyring stored passwords you enter will not safeguarded behind a master password or encryption.  Whether or not you want to do this is entirely up to you.  I personally have had enough of the keyring manager and consider it kind of annoying.  But as I said before, you may have certain environmental factors that make having a master password over the rest of your passwords a good idea.  Keep in mind that the keyring password manager has absolutely nothing to do with your administrative/root privilages password that has to be entered any time you want to apply updates, or add/remove software.  You will still have to type your account password in for these actions, and that is something I am quite comfortable with. I’m just happy I don’t have to have to ask my girlfriend to type in a keyring password every time I want to restart the computer while I’m away from home.

---

### Post by Gargintua on 2010-02-05
I think i might try this in a sec, coz keyring manager is spamming me

---

### Post by Foxblood on 2010-05-01
Thanks,snkiz, that worked well for me.

---

### Post by mcsenna on 2010-05-04
Great thanks, worked for me too.

---

### Post by mcsenna on 2010-05-04
Great thanks, worked for me too.

---

### Post by firesock on 2010-09-12
Thank you very much!! it worked perfect!!

---

### Post by Chrispy764 on 2010-11-09
Thanks, I was wondering about this and searched before I posted my question.

---

