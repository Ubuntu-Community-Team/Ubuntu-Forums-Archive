---
title: "Customizing mount"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by cong06 on 2008-05-13
I'm in a College network, with several computers that share out several folders. About 3-4 different ones, each with about 3-7 folders shared.

I'd like to mount them all for quick navigation, but I also like organization...

Ideally I could mount simply the computer...but it seems that doesn't work...
ie:
**//<IP_Address>/ /mount/point**
instead of:
**//<IP_Address>/folder /mount/point**
fails. You need to mount the folder of the computer.

So for now I have a set up like this:
**//<IP_Address>/folder /mount/point/folder**
cause I have several computers, and several have folders called: "games" "movies" etc. This way there's at least hierarchical order.

The only problem with this is that It leaves several folders on the desktop, and I get a bit confused...
Can I have only <point> show up instead of all ~5folders x 4computers?

Does that make sense?

---

### Post by nixscripter on 2008-05-14
I have solved this problem in a somewhat hackish way, but it might work for you. It is a simple shell script, which I will call remote_mount, and it manages mount points and acts as a toggle.

For example, I run the command: ```
remote_mount //my-server/dir
``` and if it's not mounted, it will create a folder **my-server** on the desktop (which is an IP in my case) and a folder called **dir** inside it. If it's already mounted, it will unmount and clean up the folders.

Unfortunately, it's not very pretty, doesn't handle errors very well, and would have to be modified for your situation.

Additionally, I believe there is a way for gnome-mount to accomplish this, but I've played with it a lot, and have been unsuccessful.

---

### Post by cong06 on 2008-05-14
Well, the one solution I did think of was to remove all auto-mounts from making icons on the desktop...

Then I could just make shortcuts to the folders that I actually wanted.

Does anyone know how to do *that?*

---

### Post by cong06 on 2008-05-16
well, my crack was to:

[remove the icons from the desktop]("http://ubuntuforums.org/showthread.php?t=795877"), and simply make shortcuts to the simulated "computer."

When it mounts it doesn't show it's icon on the desktop. Instead I have icons that show there all the time.

It's probably uglier then your idea, but eh. Mine is faster. and these are servers that are rarely down...

---

