---
title: "Could not update ICEauthority after Evolution import"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by aa4bb on 2010-04-23
9.10 on a Dell Latitude D620 was fine until I tried to import my Thunderbird email into Evolution. The process did not go to completion and I don't remember now how I terminated it. At any rate, when I next booted, I got the message "Could not update ICEauthority file /home/user/.ICEauthority", where user is my username. It went ahead and started up as though it was going to work, but when I tried to start Firefox, it said Firefox was already running and had to be shutdown before it could be restarted.

So, I began search on the ICEauthority problem through Google. There were a number of postings with remedies such as 

sudo chown -R user:user /home/user/.*

or

logging into root and

chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit

These didn't work for me. I had a second user that I was able to log into and it worked OK for a while, but as I kept trying different things I found, the second user began to trigger the ICEauthority message and further "There is a problem with the configuration server (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)".

More research. One suggestion was to add another user, give it admin privilege, copy files over to the new user and delete the old admin account. The result was getting the same ICEauthority error for the new user as well.

I'm many hours into this and not too optimistic that I can resolve it by continuing to putz around. Is there a orthodox (or should I say "canonical") way to just reinstall 9.10 from CD that will preserve my data and installed programs and get this fixed?

---

### Post by ajgreeny on 2010-04-23
Using nautilus as your user have a look at the properties of the .ICEauthority file in your home, to see if you are the owner and what permissions you and others have.  To see hidden files you may need to use Ctrl+H.

On my system that file is owned by me with read/write permissions, and group and root permissions are set as none.  So use command ```
sudo chown user:user /home/user/.ICEauthority
``` Then if needed you can use nautilus, once you are the file owner, to set permissions for group and root to none, or command ```
chmod 700 /home/user/.ICEauthority
```

---

### Post by aa4bb on 2010-04-23
Thanks ajgreeny. I was able to get my main user account going again with the assistance of your suggestions, though not exactly what you described.

I see now, using nautilus, that all folders under /home/user (i.e., Documents, Downloads, Music, etc) have a Lock icon next to them and when I look at permissions for each of these, it shows Access Files, not Create and Delete. Also when I try to start Firefox, it says "Firefox is already running but not responding. To open a new window, you must first close the existing Firefox process or restart your system". However, when I restart my system, it gives this same message again.

I think I must have caused some of these problems by trying to apply the solutions posted by others.

---

### Post by ajgreeny on 2010-04-23
OK then, now try in terminal ```
sudo chown -R user:user /home/user
sudo chmod -R 755 /home/user
```

---

### Post by aa4bb on 2010-04-23
I got the error message :

chown: cannot access '/home/user/.gvfs' : Permission denied

---

### Post by ajgreeny on 2010-04-23
Ignore that for the moment and see if you can get things running properly again.

I think that is just a virtual folder renewed every time you boot, so the permissions for that are set at boot time.

---

### Post by aa4bb on 2010-04-23
I went ahead and did sudo chmod ...

It gave me a message about .gvfs also. However,  I went ahead and rebooted and logged into the account.

Now, Firefox loads fine and things seem back to where they were before.

Thanks very much!

---

### Post by ajgreeny on 2010-04-24
Great!

I'm glad you are back with all things running as they should.

---

### Post by afrodeity on 2010-07-15
> **aa4bb said:**
> I got the error message :

chown: cannot access '/home/user/.gvfs' : Permission denied

I get the same .gvfs message.

Notice that its failing to update /var/lib/gdm/.ICEauthority which doesn't exist.

I only have an .ICEauthority in my home folder, so I suspect there is something wrong with the configuration of the 
 configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 which exits with status 256)

Changing ownership of my home folder hasn't worked.

Changing ownership of my tmp folder hasn't worked.

Need to reconfigure something.

---

### Post by afrodeity on 2010-07-15
Solved my problem like this.

```


sudo chmod 775 /etc/gconf*

sudo apt-get install --reinstall gdm

```

---

