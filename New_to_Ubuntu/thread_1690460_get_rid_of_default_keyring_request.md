---
title: "get rid of default keyring request"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by hollowtd on 2011-02-18
Everytime I log in or power on, I have to type in my default keyring like 3-4 times. Is there anyway to make it so it quits asking me to type this in everytime? Why does it ask so many times? Ubuntu 10.10

---

### Post by uRock on 2011-02-18
Do you have your system set to log you into your account automatically?

---

### Post by hollowtd on 2011-02-18
Yes, thanks

---

### Post by matt_symes on 2011-02-18
Hi

I had the same problem the other day when installing 10.10 on a friends PC. Go to Passwords and encryptions keys. 

On 10.04 it's under Applications->Accessories->Passwords and encryption keys but, if i remember rightly, it's under System->Preferences on 10.10. Start it up. 

If you have more than one folder under Passwords then you have the same problem i had. I had two 'Login' and 'Default'.

What you want is all your keys to be under the Login folder. Either move or delete all the keys until only the keys under login are left and only Login folder is left. 

Then your login password will automagically unlock you keyring when you logon.

Kind regards

---

### Post by hollowtd on 2011-02-18
I'll give it a try. Thanks

---

### Post by hollowtd on 2011-02-18
I have two folders:

One says: Passwords: Login

Under that one it says: Passwords: default (with the little arrow that you can click to show you all the keyrings) 

Do I want to move any of these around?

Thanks

---

### Post by matt_symes on 2011-02-18
Hi

> **hollowtd said:**
> I have two folders:

One says: Passwords: Login

Under that one it says: Passwords: default (with the little arrow that you can click to show you all the keyrings) 

Do I want to move any of these around?

Thanks

Yep. You have the same problem i had. If remember rightly, i tried to move the keys under default to under login. It would not let me (but i did not try hard). The only key i had under default was the key for my wpa wireless network. What i did was disconnect my wireless connection, delete that wireless key under defaults and then delete the defaults folder.

After that i tried to reconnect to my wireless network. It asked for the wireless key again and this time it stored it under the Login folder in the keyring.

Kind regards

---

### Post by hollowtd on 2011-02-18
I'll give that a try too. Thanks

---

### Post by heyho on 2011-02-18
It's usually for your wireless key.  To prevent this, I go to edit connections (right click on signal strength bars), select your wireless connection, edit, and check the box at the bottom which says something like "make available to all users".

When you have closed the window, the connection will drop - simply re-connect, and all should be good.

---

### Post by hollowtd on 2011-02-18
I'll do that too. Thanks again.

---

### Post by hollowtd on 2011-02-18
It still asks me once to type in the password. That's better than 4 times.

---

### Post by matt_symes on 2011-02-18
Hi

Alright, try this. Right click on the login folder on the password and encryption keys dialog and select change password. Make sure it is the same as your logon password.

Kind regards

---

### Post by asadullah on 2011-06-15
Many thanks for this thread. What I ended up doing to get it to work on ubuntu 11.04 on a gateway nv52 ( don't know if computer type matters) is select login automatically and then open up the passwords and encryption keys I had two folders in there login and default I deleted the default and then rebooted. Upon reboot I had the same 3 things plus an additional on or two I clicked on more and selected .... unlock this everytime I log in then entered my password. after I did this for everyone I rebooted and was good.   

I had this problem with network manager for awhile but found a solution several releases ago. If you right click the network and wireless button and then edit connections select your connection and choose edit then select available to all users and that solved that hope this helps others and maybe myself if i forget

---

### Post by lekksi on 2011-06-16
I had the same problem with password prompts during startup.
I previously had the automatic login on, which I think caused all my stored passwords to go to a keyring named "Default" instead of the login keyring.

As I didn't find a way to copy the passwords from one keyring to another with seahorse I tried renaming the keyring files in ~/.gnome2/keyrings. And now the keyring is opened as I login.
NOTE: As [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") said, the keyring and login passwords have to be identical.

What I did was:
```

cd ~/.gnome2/keyrings
rm login.keyring
mv default.keyring login.keyring
echo -n "login" > default

```The last echo sets the login keyring as default, this can be achieved with seahorse aswell.

I didn't try to merge keyrings as I didn't have any passwords saved in the login keyring. Has anyone tried merging? A quick look at the keyring file suggests that simple cat keyring_1 >> keyring_2 will not work.

---

### Post by sompo on 2011-06-16
> **uRock said:**
> Do you have your system set to log you into your account automatically?

you may need this add-ons that called lasspass....it very cool plugin that i have installed...it suitable for firefox.
[https://lastpass.com/misc_download.php](https://lastpass.com/misc_download.php)

---

### Post by lekksi on 2011-06-16
> **sompo said:**
> you may need this add-ons that called lasspass....it very cool plugin that i have installed...it suitable for firefox.


The plugin is - as you said - for Firefox (btw. available for other browsers as well).
The problem we are dealing with in this thread is not with saved passwords in a web browser, though.

---

### Post by ExileAmongYou on 2011-06-16
> **lekksi said:**
> I had the same problem with password prompts during startup.
I previously had the automatic login on, which I think caused all my stored passwords to go to a keyring named "Default" instead of the login keyring.

As I didn't find a way to copy the passwords from one keyring to another with seahorse I tried renaming the keyring files in ~/.gnome2/keyrings. And now the keyring is opened as I login.
NOTE: As [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") said, the keyring and login passwords have to be identical.

What I did was:
```

cd ~/.gnome2/keyrings
rm login.keyring
mv default.keyring login.keyring
echo -n "login" > default

```The last echo sets the login keyring as default, this can be achieved with seahorse aswell.

I didn't try to merge keyrings as I didn't have any passwords saved in the login keyring. Has anyone tried merging? A quick look at the keyring file suggests that simple cat keyring_1 >> keyring_2 will not work.

This is a fantastic solution. I've had this problem multiple times over the last few Ubuntu installs and I think I usually ended up just removing the default keyring password and storing the passwords unencrypted to avoid dealing with the hassle. Thanks!

---

### Post by mp035 on 2011-08-20
> **lekksi said:**
> I had the same problem with password prompts during startup.
I previously had the automatic login on, which I think caused all my stored passwords to go to a keyring named "Default" instead of the login keyring.

As I didn't find a way to copy the passwords from one keyring to another with seahorse I tried renaming the keyring files in ~/.gnome2/keyrings. And now the keyring is opened as I login.
NOTE: As [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") said, the keyring and login passwords have to be identical.

What I did was:
```

cd ~/.gnome2/keyrings
rm login.keyring
mv default.keyring login.keyring
echo -n "login" > default

```The last echo sets the login keyring as default, this can be achieved with seahorse aswell.

I didn't try to merge keyrings as I didn't have any passwords saved in the login keyring. Has anyone tried merging? A quick look at the keyring file suggests that simple cat keyring_1 >> keyring_2 will not work.

+1 for this solution.  Thanks.  (This thread should probably be marked solved.)

---

