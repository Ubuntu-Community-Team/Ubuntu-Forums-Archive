---
title: "&quot;Failed to run (application) as user root.&quot;"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by gnometorule on 2011-08-24
I've recently come across issues I don't remember having in the past. 

(1) When trying to run certain applications from the "Application" menu, I get feedback of the following sort (imagewriter is just an example):

Failed to run imagewriter as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

(2) When trying to run from the command line (sudo imagewrite), I hear:

(name) is not in the sudoers file. This incident will be reported.

(3) When trying to go to certain options in the Administration menu (e.g., "Software sources"), I get the same feedback as in (1).

I have no trouble switching to su privileges on the command line, or between the users I created.

What is going on? What do I need to do to make this go away? Many thanks.

---

### Post by sanderd17 on 2011-08-24
It seems you're not anymore in the sudoers group and that you activated the real root of your system.

Check your /etc/sudoers file, it should look like this:
```

# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d


```

Which means that all users in the admin group can use the sudo command (become root). If this file is correct, check that you are in the admin group.

---

### Post by gnometorule on 2011-08-24
The order was slightly different, and some "ALL" were "ALL;ALL" and vice versa. I changed it to mirror yours. The problem persists.

---

### Post by sanderd17 on 2011-08-24
> **gnometorule said:**
> The order was slightly different, and some "ALL" were "ALL;ALL" and vice versa. I changed it to mirror yours. The problem persists.

And did you check if you belong to the admin group?

---

### Post by gnometorule on 2011-08-24
That's adm, right? I wasn't and added myself. Still the same problem. I did notice that all groups seems to have no members. Shouldn't the su at least be a member, or is that by default?

In any case, still the same problem. Should I add myself to more groups? If yes, which ones?

Thanks much.

---

### Post by gnometorule on 2011-08-24
It seems to work now, after going this way (on my system, 10.04):

System->Administration->Users and Groups->Advanced->Allow user to administer system

This is pretty much what you suggested. I'd still be interested in understanding how this could have been done from the command line, if anyone got an idea.

Many thanks.

---

### Post by SavageWolf on 2011-08-24
If you are not in the group "admin" (not "adm", I think that's different...), then the only way to get back into that group would be to ether log into a recovery session thing or live CD.

---

### Post by gnometorule on 2011-08-24
:)

Here is how my group file looks like...I don't even see a group admin, but it must exist?

```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:ralf
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:

```

---

