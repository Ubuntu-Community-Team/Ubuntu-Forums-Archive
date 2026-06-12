---
title: "Shared Files"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by a1tone on 2007-05-27
Hi

Hope someone can help.

I have a Laptop running Windows XP, connected to the internet wirelessly. I also have a wired PC using Untuntu.

I am using a D-Link Router.

I can see all my XP file on the Ubuntu PC, but as I'm new to Ubuntu, only been using it for a week, I'm not sure how I can make the Ubuntu files viewable on my XP Laptop.

Thanks in advance.

---

### Post by RudolfMDLT on 2007-05-27
Hi there, 

there are a couple of ways to do this - I personally prefer editing the textfile that control Samba. Anyway - find the folder that you would like to share, right click on it and click "Share this folder". Slect to install Windows/Samba. you can untick NFS. then just select the folder you would like to share with the option you want that accompany the share. 

Post back with results! :)

Cheers,

Rudolf

---

### Post by Wiebelhaus on 2007-05-27
First install samba

sudo apt-get install samba

With this you will have samba installed on your system, now you need to edit the configuration file which is located at:

/etc/samba/smb.conf

Here I will put a simple minimal configuration to allow share files from your Linux server.

 

> [global]

workgroup = MSHOME

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/USERNAME IN LOWERCASE

 

read only = No

guest ok = Yes

 

 

    * workgroup; Lets you specify the windows workgroup
    * netbios name; Lets you specify the name with your Linux PC will be seen by windows PCs
    * security; specifies the level of security, default is user, but if the users on the windows PCs are not the same as the ones on the Linux PC, you better use share instead
    * auth methods; Possible options include guest (anonymous access), sam (lookups in local list of accounts based on netbios name or domain name), winbind (relay authentication requests for remote users through winbindd), ntdomain (pre-winbindd method of authentication for remote domain users; deprecated in favour of winbind method), trustdomain (authenticate trusted users by contacting the remote DC directly from smbd; deprecated in favour of winbind method)
    * domain master; Lets you configure your PC as a domain master or not, in this case we prefer not, as our goal is only to share files
    * wins support; If you want or not to have wins enabled or not

Now comes the shares section, the string you put between the [] will be how windows will sees the share, in this case share1

      path; You put here the path you may want to share

      read only; yes or no, depending if you want to permit other users to write on this directories.

      gest ok; It is a boolean field, and will permit or not guest users to access this resource

______________________________________________

For simple sharing that is all that is needed_____________

---

### Post by a1tone on 2007-05-27
Hi

I have tried to access the /etc/samba/smb.conf which was fine, but when it came to saving. It says I don't have the permission to do it.

---

### Post by azteech on 2007-05-27
> **a1tone said:**
> Hi

I have tried to access the /etc/samba/smb.conf which was fine, but when it came to saving. It says I don't have the permission to do it.

From a terminal window, you need to open the smb.conf file with the editor of your choice using the sudo prefix ... like this

From menu, select Applications > Accessories > Terminal

This will open up a new terminal window. In the terminal window type the following:

sudo gedit /etc/samba/smb.conf

You will then be prompted to enter your password.  Enter your password, and the editor will open your smb.conf file in write mode. After making the recommended changes you will be able to save the file.

Note: In the example above, I elected to use the gedit text editor. You can use another editor (e.g. nano, vi, etc.), if you are so inclined.

---

