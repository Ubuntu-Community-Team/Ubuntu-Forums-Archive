---
title: "Timed restart on login"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by jobromedia on 2009-09-22
Howdy! I've got assigned to develope a custommer computer to be placed in the reception area of our office. This computer is mostly for letting the clients contacting the person assigned to him via email. To prevent the computer being used for other purposes I need to:


[LIST]
[*]Enable a timer to reboot the computer after a specified time.
[*]Prevent the users from tampering with the timer giving them more time than allowed.
[*]I also need this timer to only be applied to specific accounts, so admins can work outside these obligations.
[/LIST]
Is there any way that this can be arranged?

Thanks in advance.

---

### Post by Cheezespread on 2009-09-22
If I understand you correctly , you can add a script to be run as an entry in the crontab ( The scheduler ) . The script can check the uptime and username ( I believe the environmental variable USER can be used) for the current user and reboot at the specified uptime. This is just an idea which comes to my mind. There would be easier and better options available. I hope some one answers this soon ; i would love an answer to the same as well.

---

### Post by Paddy Landau on 2009-09-22
> **jobromedia said:**
> I also need this timer to only be applied to specific accounts, so admins can work outside these obligations.Is there any way that this can be arranged?
This last one has me befuddled. What if you (the admin) sign in, and then sign out? Must the timer restart from where it left off?

Anyway, here's my suggestion, which I suggest you experiment with.

[SIZE=2]**Concept**[/SIZE]

[LIST=1]
[*]Create a cron entry under root (so that only admins can get at it) to reboot after the time period (for the sake of this discussion I'll assume one hour). However, if it has been asked (by an admin) to suspend, it waits.
[*]Create a script to suspend the reboot script (only accessible to admins).
[*]Create a script to resume the reboot script (only accessible to admins).
[/LIST]
For the purposes of this discussion, let's call the scripts respectively *rebootme*, *rebootsuspend*, and *rebootresume*.

[SIZE=2]**Implementation**[/SIZE]

/root/rebootme:
```
#!/bin/bash
rm -f /root/rebootme.suspend # In case you forgot before you last rebooted.
while [[ 'x' ]] # Forever
do
    sleep 1h  # Sleep for one hour.
    if [[ ! -f /root/rebootme.suspend ]]
    then
        reboot # Reboot now.
    fi
done
```Now create an entry in cron using sudo to run this script on bootup.
```
@reboot /root/rebootme
```/root/rebootsuspend
```
sudo touch /root/reboot.suspend
```/root/rebootresume
```
sudo rm -f /root/reboot.suspend
```Finally, stick an alias to each of */root/rebootsuspend* and */root/rebootresume* into your *.bashrc* in order to make it easier for you to run.

Warning: I haven't tested this, so be sure to test thoroughly.

---

### Post by Paddy Landau on 2009-09-22
> **Cheezespread said:**
> The script can check the uptime and username ( I believe the environmental variable USER can be used) for the current user and reboot at the specified uptime.
Clever idea. I'm not sure exactly which commands and variables could be used to determine which user is logged in, and whether the user is an admin.

---

### Post by Cheezespread on 2009-09-22
1.uptime - Tell how long the system has been running. ( from man pages )
2.USER - the environmental variable gives you the username.

If there is a list of users who are admins , you could verify the current username against the admin list.

like 
```

if ( "$USER" != "<adminusername>") 
         then 
                reboot 
fi

```

Use cron to check the uptime and run the script ( I am not so good at this ) . Wouldn't that do ?.

But can an admin setup a cron to be run on any user login ? Hope anyone can help !

---

### Post by astrakhan on 2009-09-22
> **jobromedia said:**
>  I also need this timer to only be applied to specific accounts, so admins can work outside these obligations.Is there any way that this can be arranged?

i think you could assign admins to a special admin group and make the script check if current user is in this group... then the script could either start the timer or cancel it depending on whether we're dealing with an admin or not.

groups are kept in the /etc/groups file. to find out which groups a current user is a member of, you can:
groups $USER
or
cat /etc/groups | grep $USER

maybe this help?

---

