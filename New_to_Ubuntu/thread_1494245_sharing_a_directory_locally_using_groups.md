---
title: "sharing a directory locally using groups"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by holocene on 2010-05-26
Greetings,

As a learning exercise, I wanted to ensure that I understand the permissions associated with sharing a directory. 

This is modeled after [http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-users-groups-private-groups.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-users-groups-private-groups.html)

My scenario is to have a root created directory that can be shared, with users assigned to a special group, and the  directory assigned that group.

My problem is that I get a permission error when my users attempt to create a file. 

What is wrong with the following shell script?

#!/bin/bash
sudo /usr/sbin/groupadd accounting
sudo mkdir /var/Accounts
sudo chown -R root.accounting /var/Accounts
sudo /usr/bin/gpasswd -a holocene accounting
sudo /usr/bin/gpasswd -a libraryu accounting
sudo chmod 775 /var/Accounts
sudo chmod 2775 /var/Accounts

After I run this, executing this code as user holocene results in:
holocene@crypt:/$ cd /var/Accounts/
holocene@crypt:/var/Accounts$ touch myfile.txt
[COLOR=Red]touch: cannot touch `myfile.txt': Permission denied[/COLOR]

Here is what the /var/Accounting directory looks like:
drwxrwsr-x  2 root accounting 4096 2010-05-26 17:08 Accounts

I verified that my users are in the accounting group by running
groups <userid>

I even verified that System|Administration|Users and Groups shows them there.

I don't know what to do next. 

Any ideas
Steve.

---

### Post by bodhi.zazen on 2010-05-26
IMO you are better off learning to use ACL .

[http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

        The link ^^ is a nice discussion, see post #9 for ACL.

    GUI tool : eiciel

        [http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html](http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html)

---

### Post by holocene on 2010-05-26
> **bodhi.zazen said:**
> IMO you are better off learning to use ACL .

[http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

        The link ^^ is a nice discussion, see post #9 for ACL.

    GUI tool : eiciel

        [http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html](http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html)

Bodhi.zazen,

I will research ACL, but I want to understand this first!

I don't know why, but it works now. On a whim, I rebooted. 

Is there something about permissions or groups that would require an exit or logout? 

Regards
Steve.

---

### Post by Nythain on 2010-05-26
group changes on users dont go into effect untill after a reboot, at least they never have with me

---

### Post by sisco311 on 2010-05-26
> **holocene said:**
> 
Is there something about permissions or groups that would require an exit or logout? 


Yep, after adding/removing a user from/to a group, it's necessary to log out for the changes to take effect.

---

### Post by holocene on 2010-05-26
> **sisco311 said:**
> Yep, after adding/removing a user from/to a group, it's necessary to log out for the changes to take effect.

Does this reboot/logoff have something to do with Ubuntu, or does this apply to all distributions and/or UNIX?

Thanks.

---

### Post by bodhi.zazen on 2010-05-26
You do not really need to either log out, and certainly not reboot.

There are two issues:

1. Permissions. If you change permissions on a file or directory, the effect is immediate. No need to either log out or reboot or start a new shell.

2. New group memberships. New group memberships do not take effect until you start a new shell.

In non-technical geek babble, Your graphical session was started under the old permissions, you need to log out and back in for your graphical applications to honor the new groups you may have added or removed.

Linux is not windows and you rarely need to reboot. Typically a reboot is needed after updating your kernel.

---

### Post by Nythain on 2010-05-26
yeah yeah, reboot was bad wording :P since i never really "reboot" (well at least as little as humanly possible) i've gotten into the bad habit of referring to restarting my X session as "rebooting" :(

---

### Post by holocene on 2010-05-26
bodhi,

I did a "man groups" and it seems to agree with your instruction to logoff. 

I remember doing a group <userid> and the groups membership seemed right. This reads the /etc/group file directly. 

Doing a "group" with out the <userid> did not show the new group membership. I believe because it is reporting the groups that the shell was started with. 

I hope I have this right.
Steve.

---

### Post by sisco311 on 2010-05-26
On a side note: I have noticed that policykit reads the user's group membership directly from the /etc/group file. i.e. if you remove your user from the admin group via users-admins you lose the ability of authenticating yourself as an admin via policykit, but you can sill use sudo to re-add your user to the admin group.  

> **holocene said:**
> Does this reboot/logoff have something to do with Ubuntu, or does this apply to all distributions and/or UNIX?

Thanks.

It applies to all (or at least the majority of) Linux/Unix platforms.

---

### Post by holocene on 2010-05-26
Thanks to all.

Steve.

---

### Post by bodhi.zazen on 2010-05-26
> **holocene said:**
> bodhi,

I did a "man groups" and it seems to agree with your instruction to logoff. 

I remember doing a group <userid> and the groups membership seemed right. This reads the /etc/group file directly. 

Doing a "group" with out the <userid> did not show the new group membership. I believe because it is reporting the groups that the shell was started with. 

I hope I have this right.
Steve.

yes, that is correct.

---

