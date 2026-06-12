---
title: "Enter password to unlock your login keyring"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by ursoouindio on 2010-08-03
*The password you use to log in to your computer no longer matches that of your login keyring.*

I would like to understand and manage whatever this keyring is about.

I've been using (for some weeks now) this pc, at first it already has an old Ubuntu installation on it and someone else has configured it in order that my user (that he configured and used some simple password) had the needed rights to administrate it. Then (on the same week), I thought it was convenient to format it and reinstall a newer Ubuntu. During the installation, it got my user's configurations.
Now, suddenly, I started to get this messages and have to insert that very first password that the other person have chosen to me, as the *keyring password*.

I've had this kind of problems other times (at home, in other pcs...), and never found where to find this *keyring* thing and what exactly it does.

I've passed the phase of getting annoyed by it, so now I would like to understand it and make a proper use of it.
How do I manage it?
How can I change the *keyring* password to match my login password? (as I believe it is how it doesn't disturb when it isn't needed)

Thanks!

---

### Post by mcduck on 2010-08-03
The keyring is used to store passwords, encryption keys and stuff like that for all programs. The idea is to keep them all in one place, and automatically encrypt them when you re not logged in to make sure nobody can get your passwords even if they are able to read the contents of your computer.

IF your keyring password and login password are set to same, the keyring will be unlocked automatically for you when you log in. If the password are different, or you use automatic login, you need to give the keyring password when some program tries to unlock the keyring. Usually this happens immediately when you log in, when the Network Manager tries to get the key for wireless network from the keyring.

To change the keyring password you can simply go to Applications/Accessories/Passwords and Encryption Keys. Right-click the "Passwords:login"-keyring and select "Change Password".

Edit: If you use automatic login, and don't want to type in your keyring password, you can just leave the fields for new password empty. That will store keys in unencrypted format, losing most of the security, but if you use automatic login then you probably don't worry about security anyway. otherwise just set the keyring password to same as your login password.

---

### Post by ursoouindio on 2010-08-03
Thank you, mcduck! :)

I've made the change you suggested, it accepted the old password and I changed it to the same password I use to login. I believe it will behave now.

Maybe its just me, but I think this *keyring* thing quite confusing.
Whenever there is some problem with passwords it mentions the keyring, while there isn't (I think so) a "*keyring*" configuration anywhere.

Also, (just an opinion) this *Password and Encryption Keys* configuration should be on the *System* menu, under *Administration*. I had found it earlier  where it is, but it was the last place where I searched for. And also, when I found, it didn't seem to be about that "*keyring*". If it was clearer, I wouldn't need to ask here.

---

### Post by mcduck on 2010-08-03
I agree that System/Preferences would be a better place for the Passwords and Encryption Keys -tool (Preferences instead of Administration since the Administration-menu is for admin tools that affect the whole system and all it's users, while the user's personal settings are under the Preferences-menu. And every user has his own keyring). Actually I always move it to System/Preferences myself. I sure don't know why Gnome developers choose to keep it under the Applications-menu.

---

### Post by naomibrown on 2010-08-04
Thanks for your reply! This was helpful to me today :)

---

### Post by oenghus on 2010-08-05
mcduck,

Another voice adding thanks for your help.  In my case, it seemed I started having troubles with the keyring when I upgraded to 10.4.

I was not able to actually change my password so I deleted it, restarted, and created new passwords and keyrings from scatch.  It worked like a charm.

Thanks again!

---

### Post by jpaugh64 on 2010-08-21
Hello. I am having similar trouble with my login keyring: It prompts me to enter it when I log in. However, I have just made a clean install of Lucid Lynx, and have never changed my password--either for the login keyring or to log in. Any ideas?

---

### Post by ursoouindio on 2010-08-22
Me too.
Although I have fixed it at work, I still have this kind of problem at home.

I needed to change the login and administrator password to a trivial one, because it is more convenient to everyone who uses that pc.

So, since the password is too simple, I needed to change with the following commands: (ubuntu doesn´t allow you to choose a simple password)
$ sudo passwd *****
$ sudo passwd myuser *****
(the same password)

And changed the one in the Accessories/Passwords to the very same password.

But it keeps asking for the keyring password (which is the trivial one) when trying to connect to the wireless network.

---

### Post by ursoouindio on 2010-09-01
Any idea how to solve this keyring annoyance?

Maybe to reset the keyring/administrator/login passwords all at once??

---

### Post by Wellis on 2010-09-08
Many thanks for the info. I followed your instructions and now keep my fingers crossed.

---

### Post by bythebay on 2010-09-10
I had a very similar problem.   Dell netbook 10n, removed remix and installed 9.10

Every thing was fine until I installed a wireless router and set encryption on.

To make a Long story made short--

I have three accounts set-up on the Dell, one with all privileges, the other two with only internet access.  It turned out that ONLY the admistrator could access the wireless lan, and there the password for the lan had been 'remembered'.

I finally found that logged in as administrator I could:
select 'preferences'
select 'network connections'  there
select 'wireless' in network selections
select ' our wireless '
select 'edit'
Then the admin PW had to be re-entered

and low and behold at the bottom of the 'edit' screen was a check box to share "available to all users"

Now the limited accounts do not even have to enter the wireless password.

Hope this helps someone

---

### Post by beew on 2010-09-10
Go to Places > Home. Check "Show Hidden Files". Then find the folder .gnome2, open it and delete the keyring folder (it will regenerate itself) Next time when you need to access the internet it will show up and ask you to set a password and you can reset it. You can choose your login password, a different one or don't enter anything, in that case it will warn you about unsafe password storage and if you just click OK it will never bother you again.

I am sure someone would disagree but for me the keyring is nothing but a  nuisance, I am not the CIA and I don't need that much "security",  a  single password prompt would be enough for me!  So I just entered nothing and use unsafe password storage. Haven't heard from the keyring manager for quite a while. :)

---

### Post by ursoouindio on 2010-09-10
beew, thanks for the suggestion. I'll try your solution and hope to also never hear of the keyring again (or at least until it is really needed, what would be very rare for me)

I don't think it is useless, even for the most users who don't need to bother that much with security. Linux is supposed to be secure and it is part of its philosophy. Being able to set the same password for login and keyring is already good - when it accepts on login at once.

But I really think this keyring thing should be easier to set up. I don't know if it is about ubuntu or gnome itself, but it is something very common to turn into a problem and I don't think there's a place to manage it efficiently.

---

### Post by gasparov on 2010-09-15
Hi,
  saving in plain text could be an issue in multi user environments.

In my opinion there is something wrong on how ubuntu handles the keyring in some occasions. For example in my case the Login keyring was empty and everytime I logged in I had to open the Default keyring hence I was asked for a password. This system was a member of an active domain that could have screwed things up.

Usually you should have your passwords under the login keyring or "Unlock password for default keyring" this way when you login the "Login" keyring is opened and since it contains the password for the "default" you can access that keyring as well.

---

