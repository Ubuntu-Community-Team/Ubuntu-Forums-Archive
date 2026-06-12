---
title: "can I change username"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by rng on 2011-06-08
By mistake, at installation of ubuntu, I named the default user as 'home' and now my home folder is /home/home! How can I change this username?

---

### Post by grahammechanical on 2011-06-08
I am not sure if this is the way to do it, but I guess that one way is to go to Users and Groups and add yourself as a user. Make sure that you set the account type to Administrator. Then shutdown and reboot and log in as your new self. Now you need to transfer any important documents that you have in /home/home into /home/you as the user. You do not want to lose data. Finally, when you have tested yourself as the user/administrator you can delete the user called home.

This is my guess. Others on the forum might like to confirm or suggest a better way. I have never been in your situation so I cannot speak from experience. By the way you find Users and Groups under System Settings in the shutdown menu in 11.04

Regards.

---

### Post by nothingspecial on 2011-06-08
Well, you would need to add a new user to change your user properly anyway - you can change your username but your home directory would still be /home/home.

Of course you could boot into recovery mode and do it from a root shell but if you make a mistake with your home directory in the root shell things can go from bad to worse.

I would go with what grahammechanical said as there is a lot less chance of something going wrong. You would have to change the owner of all the files you transfer to your new username though.

If you would like to do it from the root shell though I can show you ......... but I suggest you don't.

---

### Post by amjjawad on 2011-06-08
If I were you, and if it's a Fresh Installation, I would Re-Install. This could be the easiest solution. Yes, there are other solutions but Re-Installation is the easiest one.

Sorry if I couldn't help much!

---

### Post by rng on 2011-06-08
Thanks everyone. 

I will play safe and continue the present name till there is any major problem. Till now, there has been only one event when a program refused to work saying that it cannot work on 'home' folder when I was in /home/home. I changed to /home/home/temp and then it worked.

---

### Post by twopointfour on 2011-06-08
This should work:

Open Users and Groups and add a new user for yourself with your new username.

Open a terminal and do this:

```
cd /
sudo rsync -av --delete /home/current_user/ /home/new_user/
sudo chown -R new_user:new_user /home/new_user

```The first line makes an exact copy of all of current_user's files into new_user's home folder. The second line changes the ownership of all those files to your new user, which is necessary for your user to work correctly. Of course replace current_user with your current username and new_user with what you want your new username to be.

Then log out of your current user and login to your new user. Your files and settings should all be the same. Try things out and make sure everything works. Once everything seems fine, you can delete your old user.

To do this, open Users and Groups again, and delete your old user. When you're sure, you'll want to make sure all your old user's files are deleted so you can save disk space (since you copied them over to your new user's home folder). Open a terminal and type:

```
sudo rm -rf /home/current_user/
```And you should be good.

---

### Post by rng on 2011-06-08
Thanks for clear instructions. I am trying this now. I hope I come back to you thru ubuntu only and not thru windows!

---

### Post by rng on 2011-06-08
Thanks to the clear instructions, I was able to solve this problem and everything seems all right. The user delete dialog box offered to remove files, but I decided to keep them for now, just in case. (Properties of 2 folders show exactly same size and number of files).

Thanks everyone.

---

### Post by rng on 2011-06-14
I realized that wine setup has not changed and wine is still trying to find /home/home folder. Programs installed thru wine are not working anymore. Simply changing the folder name from /home/home/filename /home/new_home/filename in properties of desktop links is not working. 

I think I will need to reinstall these programs.

---

### Post by matt_symes on 2011-06-14
Hi

Did you rerun winecfg to reconfigure wine ?

Kind regards

---

### Post by rng on 2011-06-14
> **matt_symes said:**
> 
Did you rerun winecfg to reconfigure wine ?


I ran it just now. It is knowing that the username has changed, but programs already installed are still not running (for them the settings folder is still in /home/home. I don't know if I have to change something special there.

---

### Post by matt_symes on 2011-06-15
Hi

What programs are not running (names) and how are you trying to start them ? From the menu ? From the command line ?

Have you tried to run them from the command line to identify why they are not running ?

Anything newly installed after running winecfg should run successfully.

Kind regards

---

### Post by rng on 2011-06-17
I reinstalled the windows setup file in wine and it is now working all right.

---

