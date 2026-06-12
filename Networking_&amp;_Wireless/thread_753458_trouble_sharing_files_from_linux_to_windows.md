---
title: "trouble sharing files from linux to windows"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by drko on 2008-04-12
I am running ubuntu 7.10 and need to share a folder to a windows xp machine. I go to the folder that I need to share and have it set as shared with smb. When I try to access the linux machine from the windows machine is asks for some password and username. I have no idea what pass/user it wants. I have the linux machine set to be part of the domain "mshome". When I try to view the properties of my computer when in mshome in windows, it says that I do not have the necessary access rights. Could it be some security setting on the linux machine or is it something wrong with the windows machine? Any help is appreciated.

---

### Post by countrylane on 2008-04-12
You need to set up a Samba user name and password, which is not necessarily the same as your Ubuntu user name and password, which is not necessarily the same as your Windows user name and password. Basically you will need 3 different user names/passwords. You can have them all be the same if you want, but that will be less secure than if they are all different.

To set up the Samba user/pass, you can go to ADMINISTRATION>>>>SAMBA. Eneter your Ubuntu password to gain access to this tool. Once the Samba Server Configuration tool appears, PREFERENCES>>>SAMBA USERS. You will see a list of users. At this point I would add a new user with a dummy name like TEST, so that you don't mess with any of the other names that are in the list, just to see if yo can get it working and login.

Next, open a terminal and type:
sudo /etc/init.d/samba restart
You should get 2 lines of response indicating Samaba is stopping then starting.

Next go to your Windows machine and logoff, or power down/power up.  Now try to access your Linux machine, but this time when you get the user name/password box, enter TEST (or whatever name you created from above) for the username and the password for TEST. You should now be able to see your Linux files and directories and be able to move around inside them.

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

### Post by starcannon on 2008-04-13
Hang in there, the EU ruling combined with the fact that the Samba team bought the documentation from MS means that very soon this should become a seamless feature in nearly all distos (at least that's my Friday night prediction, we wont really know until Monday morning :) )

Until then try [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) and as always google is a great tool.

---

