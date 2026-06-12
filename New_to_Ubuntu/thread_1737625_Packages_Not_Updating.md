---
title: "Packages Not Updating"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by cleverlemming on 2011-04-23
For the past several days, I've been seeing a "17 packages can be updated." msg when I ssh into my server. I run apt-get update and apt-get upgrade. The next time I log in, the msg is still there. My server is remote so I only have SSH access. Am I missing something? 

Ubuntu 10.04.2 LTS
2.6.32-24-generic-pae #39-Ubuntu

---

### Post by plucky on 2011-04-24
> **cleverlemming said:**
> For the past several days, I've been seeing a "17 packages can be updated." msg when I ssh into my server. I run apt-get update and apt-get upgrade. The next time I log in, the msg is still there. My server is remote so I only have SSH access. Am I missing something? 

Ubuntu 10.04.2 LTS
2.6.32-24-generic-pae #39-Ubuntu

If there are dependency problems,try ```
sudo apt-get dist-upgrade
``` to see if that will fix it.

Good Luck

---

### Post by cleverlemming on 2011-04-25
Thanks for your response. 
Tried ```
sudo apt-get dist-upgrade
```. Nothing changed. . 

When I login via ssh, I still see the following motd:

17 packages can be updated.
12 updates are security updates.

After I run apt-get update and apt-get upgrade, I get the following message from apt-get upgrade: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And, the update message remains. Is the problem, perhaps, in the motd?

---

### Post by cgroza on 2011-04-25
It's probably a bug. Just give it some time, it may go away.

---

### Post by Coder68 on 2011-05-01
I have the same issue. On log in to 10.04.2 server, I see 23 packages can be updated and 12 updates are security updates.

Yet apt-get update/upgrade says there is no updates available. 

Must be a recent bug.

---

### Post by zeero_k on 2011-05-05
Delete file /etc/motd.tail
Problem solved.

Reference:
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827)

---

### Post by SlimBiggins on 2011-05-18
I have the same problem. I'm running Ubuntu Server 10.04.2 LTS (x86). I updated the list of repositories, then tried both upgrade and dist-upgrade. I know the packages didn't install, because there would have been output to the terminal during the process.

Simply deleting the MOTD is like sweeping dirt under the rug. You aren't bothered with the message telling you to update your security packages, but you still need to update your security packages.

I know this is an older thread, but does anyone have any suggestions?

Thanks,
SlimBiggins

---

### Post by mcduck on 2011-05-18
> **SlimBiggins said:**
> I have the same problem. I'm running Ubuntu Server 10.04.2 LTS (x86). I updated the list of repositories, then tried both upgrade and dist-upgrade. I know the packages didn't install, because there would have been output to the terminal during the process.

Simply deleting the MOTD is like sweeping dirt under the rug. You aren't bothered with the message telling you to update your security packages, but you still need to update your security packages.

I know this is an older thread, but does anyone have any suggestions?

Thanks,
SlimBiggins

If you read the bug report you'll notice that the message is a result of the bug. Your updates are installed just fine, the MOTD file just isn't updated properly and therefore it gives you wrong information about available updates.

So yes, removing the file really is the correct and proper solution.

If you actually have problems with successfully running apt-get upgrade, that's a completely different thing and not related to this thread.

---

### Post by anuuz on 2011-06-07
> **zeero_k said:**
> Delete file /etc/motd.tail
Problem solved.

Reference:
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827)


Thanks!!! That solved my issue. :)

---

### Post by zeero_k on 2011-06-10
Update:

It happened again, and I had to delete the /etc/motd.tail file again. I THINK what might have caused it is when I logged in another terminal session while Aptitide was running an update. When I logged in that second session I got the MOTD twice! And then it got "stuck" and I had to delete that file to have it update normally. I can't confirm this at the moment since my system is all up-to-date :)

---

### Post by SlimBiggins on 2011-08-26
In case anyone is still having problems, I believe I have a sure-fire way to take care of security updates (on either Server or Desktop editions); whether at a login shell, a virtual terminal, or a remote SSH login.

Open up a virtual terminal (for Desktop users) or get to a login shell (for Server users). On my server I SSH into the shell and have preformed this procedure without fail.

First, update your sources:

```
sudo apt-get update 
```

Now, use **aptitude** to solve this problem.

Once in a shell, run aptitude:

```
sudo aptitude
```

This will bring up a CLI package manager that displays much like a directory tree. If there are Security Updates to be installed, you will see a "Security" tree listing. Scroll down to that and use **+** (plus sign) to select the entire tree for installation. A **-** (minus sign) can be used to de-select.

Use the **g** command to move to the verification screen, then use **g** again to begin the install.

**aptitude **has a command/help menu at the top that can be accessed by **<CTRL> + T**

This program works great for security updates as well as fishing around for other packages from CLI. Check **man aptitude** for more features.

-Peace
SlimBiggins

---

