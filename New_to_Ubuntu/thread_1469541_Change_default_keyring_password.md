---
title: "Change default keyring password?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by aquascrotum on 2010-05-02
Since upgrading to 10.04 I've tried to set up my empathy account - as part of this process I'm prompted for the "default keyring" password.

As far as I was concerned that password was always previously the same as my login account password, but its not being recognised as correct.

How can i find out what my keyring password is, and how can i change it?

Thanks.

---

### Post by inameiname on 2010-05-02
I'm looking into this as well, but for Evolution Mail. I've learned that your default keyring password is the same as your user password when you first install, but when you change your user password to whatever it is, the default keyring one remains the old one. And so far I've looked into two solutions:

To delete keyring entirely, and then can put in new passwords:

# killall -9 gnome-keyring-daemon
 $ rm -fr ~/.gnome2/keyrings

        or

"This is handled by right clicking on the word login in the encryptions and keyrings password window. This open a menu with the option to change password. Yes it's a little bit hard to find, if you don't know it's there."


I know the first one works, but I'm not sure if there lies a security issue. And as to the second one, I'm not entirely sure it works with Lucid. Though I haven't checked yet.


Oh, and regardless, I think you can find out what your keyring password is by checking out 'Passwords and Encryption Keys' under the 'Accessories' tab.

---

### Post by aquascrotum on 2010-05-02
Solved.

In Passwords & Encryoptions Keys manager (Applications>Accessories) - right clicked on Login Password and used selection "set as default".

---

### Post by mcsenna on 2010-05-04
H, I could use some help with this pesky keyring thing too. I tried the command you listed but the thing stillkeeps rearing its ugly head. I could not find any login password to right click on in the accessories/passwords folder either. Anyone have any ideas here?
By the way if I keep hitting "deny" over and over it eventually goes away.

---

### Post by inameiname on 2010-05-04
This is the easiest way to reset or delete it. Just go to Accessories > Passwords and Encryption Keyrings and then right click on the word "Passwords: login" and then you can either 'delete' or 'change password'. Obviously, I'd change it to the same as your Ubuntu user password. You just have to remember to do this every time you change your user password.

---

### Post by aquascrotum on 2010-05-04
> **inameiname said:**
> This is the easiest way to reset or delete it. Just go to Accessories > Passwords and Encryption Keyrings and then right click on the word "Passwords: login" and then you can either 'delete' or 'change password'. Obviously, I'd change it to the same as your Ubuntu user password. You just have to remember to do this every time you change your user password.

Surely though you need to know what the default keyring password is prior to changing it - this was my problem originally posted.  If the tool I posted that copies your login password to your keyring password doesnt work then you'd be stumped...

---

### Post by inameiname on 2010-05-04
Oh I see. Unless you've changed the default keyring password before, it should be the same as your first user password you used when you installed Ubuntu. I guess if you don't know it or remember it, then you should just delete it entirely, either with the right click way I mentioned or use the terminal :

# killall -9 gnome-keyring-daemon
 $ rm -fr ~/.gnome2/keyrings

---

### Post by mahela007 on 2010-05-15
> **aquascrotum said:**
> Since upgrading to 10.04 I've tried to set up my empathy account - as part of this process I'm prompted for the "default keyring" password.

As far as I was concerned that password was always previously the same as my login account password, but its not being recognised as correct.

How can i find out what my keyring password is, and how can i change it?

Thanks.

I had a similar problem after upgrading to 10.04. (I upgraded via the alternate installation CD). Before this, when I was using Ubuntu 9.10, the Keyring password and the login password were the same. However, after upgrading, the keyring password has changed. (And here's something really spooky.. it's changed to another password that I use regularly.)

---

### Post by rhdinah on 2010-07-18
May I just add to this [getting] stagnant thread ...

I'm afraid it's hidden, under-the-covers, user-unfriendly interfaces like this that keeps Linux in the geek-only category. Whatever extra security it offers is far outweighed by the issues and hardships it creates. :(

---

### Post by mahela007 on 2010-07-18
I agree.

---

### Post by Vanderfurff on 2010-07-23
> **mcsenna said:**
> H, I could use some help with this pesky keyring thing too. I tried the command you listed but the thing stillkeeps rearing its ugly head. I could not find any login password to right click on in the accessories/passwords folder either. Anyone have any ideas here?
By the way if I keep hitting "deny" over and over it eventually goes away.

I'm having the same problem as you, and am also getting no response from terminal when I enter those values.  any help appreciated!  many thx!

---

### Post by beew on 2010-07-23
Delete the  folder home/username/.gnome2/keyrings

You have to click view > show hidden files to see the .gnome2 folder.

Then next time when it comes up it will prompt you for a new password. You can create a new one, use the same one as your login password or just input nothing.(no, it is not by default the same as your user password, you set it the first time it appeared, maybe when you tried to connect wirelessly)

I basically set it to be blank (not input anything), it then will give a warning like use unsafe storage or something like that, just ignore it and hit enter. It never bothers me again.:p

I am sure this will horrify some security minded folks. :P

---

### Post by k.sangeeth on 2010-09-11
IMO, deleting the old keyring is not a good thing to do as as you end up loosing all the passwords it stored ..
The suggested way is to go to "Applications -> Accessories -> Passwords and Encryption keys" .. right-click on "+ Passwords:login" and do a "Change Password"; This time you can give a new keyring password, same as your login password. I think this is a more elegant way ..

---

### Post by allankelly on 2010-10-08
This is a really poor piece of UI design with no supporting documentation. First off, the "Passwords and Encryption Keys" app (seahorse) should be on the System->Administration menu. Second, changing login password should be hooked to a default keyring password change - or at least warn. Third, seahorse does loads of remote stuff 99.9% of people don't want or understand (including me). Fourth, I cannot see in seahorse how to alter the default keyring password without forum posts like these. And fifth, there is nothing helpful in the Ubuntu Help manuals (that I could find).

By geeks, for geeks. I include myself in that category but I am also a professional and a father and I lack time for this sleuthing.

Cheers, al.

---

### Post by kjetilbmoe on 2010-10-18
Deleting the entire .gnome2/keyrings directory solved this for me.

---

### Post by twistle on 2010-10-23
I agree as well.

---

### Post by BrownieBoy on 2010-11-18
For 10.10 Maverick, the  Passwords and Encryption Keyrings dialog is under System->Preferences.

---

