---
title: "NFS mounted /home/myuser over slow connection?"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by jeffk on 2008-10-06
I have a remote office connected by OpenVPN over a relatively slow upstream link (384kbps down, 5mbps up). I believe the main office is a similar connection.

To support roaming users, I mounted /home/myuser with NFS (v3 exports style, I think). The mount worked fine.

The initial GNOME login at the remote office was taking an indeterminate amount of time. I did not run the test to completion, but I expect it would have eventually come up to the GNOME environment (vnc remote desktop worked).

Is it unadvisable to mount NFS home directories over a slow link?

Would NFS caching eventually make the speed issue transparent?

BTW, I'm looking into SSHFS FUSE mounting as an alternative to NFS, for more modern handling of permissions, etc. As it is, I have all /etc/passwd UID:GID's consistent across all workstations, so NFS is working reasonably well in that regard at this time.

Thanks for any advice.

---

### Post by nixscripter on 2008-10-06
I've never used sshfs, but I can tell you about NFS performance.

You're right; caching is the secret. NFS in general works better for accessing a lot of small files instead of a few large ones. But when you log in, for example, it has to read a whole lot of stuff -- once.

If this is just to let people log into your box, I would suggest seeing if you can set up a reverse tunnel of some sort, and just allow X11 session forwarding over SSH. If they really need your home directory, my only suggestion is to play with read cache size on the NFS mount parameters (see the NFS options on the [_mount man page_]("http://linux.die.net/man/8/mount") for more details).

---

### Post by jeffk on 2008-10-16
Thanks for the feedback. Here are a few more particulars about the system, and the impressions from a few weeks of use, that might help with any advice about tuning, caching NFS vs. SSHFS:

Large Shared NFS Mounted Folder
-------------------------------

The main collaborative work location for all users is mounted nfs as (e.g.) /media/ourfiles

/media/ourfiles itself contains about 2,000 folders (few/no subfolders) with 1-3 small files in each folder. Always one small text file, increasingly one or more PDF and PNG files as their document imaging comes into wider use.

The users definitely notice a very long wait time to open /media/ourfiles the first time after login.

The machines stay on, so They wouldn't mind if subsequent access to that large folder were fast.

Access to a specific folder /media/ourfiles/customer101 is fast, but they're not in the habit of typing pathnames.

Mounting Home Directories
-------------------------

The interoffice link (OpenVPN/OpenWRT over 5Mb/384K cablemodems) is too slow to mount the (Ubuntu GNOME) user home directories from the server. Login from the remote offices might complete eventually, but I gave up after a ten-minute wait.

Mounting the home directories would be very helpful, as the users would like to be able to roam to any machine with their home environment intact.

Caching
-------

The change velocity for files is relatively small, as these are small offices. However the number of small files is large, and a small number of files are large (e.g. media files for presentations, data files under ~/.wine/).

If I could cache the contents of the NFS mounted directories at machine boot (not user login), I think the situation would be a lot better.

Thanks, especially for any tips on pre-caching NFS.

---

### Post by nixscripter on 2008-10-16
> **jeffk said:**
> 
/media/ourfiles itself contains about 2,000 folders (few/no subfolders) with 1-3 small files in each folder. Always one small text file, increasingly one or more PDF and PNG files as their document imaging comes into wider use.

The users definitely notice a very long wait time to open /media/ourfiles the first time after login.



No doubt. NFS, in preparation for requests, will attempt to try and get a listing of all 2,000 folders. That will take a while.

> 

Access to a specific folder /media/ourfiles/customer101 is fast, but they're not in the habit of typing pathnames.



A simple suggestion: get them into that habit. ;-) What NFS is asked for depends upon what things the application asks for. A shell, for example, holds open the working directory (the directory that you're "in") all the time. So, if you can jump working directories from outside the NFS mounted tree to inside one of its subdirectories (like customer101), it can save it a lot of work. You can see what your applications are up to, and find ways to optimize them with the **lsof** command.

> 

Mounting Home Directories
-------------------------

The interoffice link (OpenVPN/OpenWRT over 5Mb/384K cablemodems) is too slow to mount the (Ubuntu GNOME) user home directories from the server. Login from the remote offices might complete eventually, but I gave up after a ten-minute wait.

Mounting the home directories would be very helpful, as the users would like to be able to roam to any machine with their home environment intact.



My question is, what exactly do they need their home directories for?

If they need just a few files, then instead of "home directories" in the former case, I would suggest doing what people have been doing for ages: "network storage". Have a home directory on each machine which is temporary (e.g. tmpfs) and everything is erased from, and a separate directory for "network drive, keep all your files here" directory inside of that. This can easily be accomplished with a shell script.

If they are trying to use their home directories for a full login, that's different. Using a home directory the way it is on the hard drive involves lots of temporary files, many of which users are not even conscious of. Temporary files means lots of creates and destroys, operations which over NFS have extra overhead compared to a simple change. In that case, I repeat: set up a remote ssh/X server instead. Have a centralized location everyone logs into on "thin clients".

> 

The change velocity for files is relatively small, as these are small offices. However the number of small files is large, and a small number of files are large (e.g. media files for presentations, data files under ~/.wine/).



Sounds like you want the best of both worlds. Don't we all ;-)

I'm going to go out on a limb here, and trust you won't blame me for this advice if something bad happens. For lots of small changes, if you are **positive** no two people are going to open the same file at the same time, you can turn off file locking. Only if you are **positive** -- because otherwise data corruption will result -- can you do this. This would require assurances like everyone only accessing files with a certain application which does its own file locking, or an equally strongly enforced personnel policy. Turning this off will reduce extra overhead in checking "is someone else holding this open?" all the time. I don't know how much, but it will result in some performance improvement.

> 

If I could cache the contents of the NFS mounted directories at machine boot (not user login), I think the situation would be a lot better.


Caching is not really under user control directly. NFS simply has an algorithm to which you can give parameters. The **rsize** and **wsize** mount parameters, for example, control how much data NFS will cache. The manual page says 8192 gives you more than the default, but if you're on NFSv3 instead of v2, you might try an even bigger number. However, it's not documented what happens; try it and find out.

As for mounting at boot, you can just [_put an entry in the /etc/fstab file_]("http://www.cyberciti.biz/tips/linux-mount-remote-filesystems-automatically-at-boot-time.html") of each client. Just make sure you pick your mounting options wisely; see the **mount** manual page for more details.

Caching, I should also point out, has limited effectiveness. If you access the same file, big or small, over and over again, you'll get a lot of benefit. But even then, if two people access it at the same time, you lose it all, because it has to fetch the changes anyway. Caching is really designed not to improve throughput, but to level it off over a "jerky" connection.

Overall, since you are talking about a small pipe (384KBps), there are limits to what you can do with NFS, much less any file system. In other words, I don't think you would get much better performance if you used some sort of FTP: everyone listing directories, copy a file down, change it, upload it, repeat. The difference between that work and NFS isn't as big as you might think (except possibly having to transfer the entire file both ways instead of part of it). The real difference is in usability and application transparency.

The only real way to improve your bandwidth is to shift the load to the server itself; make the clients "thinner" and the server "fatter". An example (mentioned above) would be setting up an ssh/X server, where nothing is going over the connection except users' keystrokes, mouse clicks, and graphics data. The server managed all the files and did all the processor work. Even if that's not what you want, but it's the principle I'm getting at: by choosing NFS, you are choosing to make the clients do all the processing and have the server just store, for the price of having lots of network traffic. All the suggestions I have made are "incidental" -- making the solution match the assumptions of the problem as closely as possible.

Hopefully that wasn't too long. I sort of got on a roll. ;-) I would simply add one more thing: do experiments. Try stuff out. I've mentioned two or three things, and that's the only way to answer some of these questions.

I know this is a hard problem. I've struggled with it for quite a while. Good luck.

---

### Post by jeffk on 2008-10-19
Thanks very much for the responses, lots to read and absorb before continuing the discussion.
> **nixscripter said:**
> My question is, what exactly do they need their home directories for?
It's for the full-spectrum gnome environment in a roving-profile use case. They have a highly configured Evolution calendar, Empathy IM, gedit with snippets (to edit those 2000 text files), and of course the typical mission-critical user priorities like wallpaper and screensaver selections ;)

They're thrilled that the roving home directory profile works so well within the home-office. NFS bandwidth over the LAN is fine. We're trying to extend that capability out to the remote offices, where these users roam in rotation.

Believe me, I wish mozilla firefox and other apps would take it easy on their profile file count and size, but it's an infinitely better status quo on Linux (plain files) than Windows (opaque registry hives).

---

### Post by nixscripter on 2008-10-20
If you have computers which work well in-LAN, that's good. In that case, I would suggest basically setting up one or two as a "remote access point", something like this:

Let's say your computers on-LAN are host1, host2, and host3. I am assuming that different people can log in to host1 by sitting down in front of it, their authentication will be verified by some other network mechanism (like LDAP or whatever) and their home directories will be mounted. When they log off, it all gets undone. Effectively, these computers are "thin clients" as far as network services are concerned.

Add another computer on-lan called host4. Have host4 run an SSH server, an X server, and allow people outside the firewall to connect over SSH. When people connect, have it check their authentication over whatever standard mechanism host1 and host2 use, just as if they logged into it by sitting in front of it. When they log in to host4, it mounts their home directories on itself, like any other on-lan machine.

When they log in this way, all the users have to do is forward their X session over the SSH connection. The result is that Host4 will do all the processing as if they're sitting in front of it, get the good throughput to their home directories, and send comparatively little (just the X graphics data) over the connection.

If X is too clunky, depending on the application, VNC works too. The point, though, is that the users shouldn't have to send all the data over the connection, just the control/graphics part. Besides, depending on how demanding your users are, many can log into the one host4, saving you overhead.

That's my advice. If you like the idea and need help, I'll see what I can do.

---

