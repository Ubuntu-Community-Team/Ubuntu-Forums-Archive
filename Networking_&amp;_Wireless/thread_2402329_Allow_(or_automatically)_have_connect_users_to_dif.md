---
title: "Allow (or automatically) have connect users to different samba shares w/out sudo"
date: 2018-09-28
forum: Networking &amp; Wireless
---

### Post by delphis on 2018-09-28
Running bionic - not sure why "Feisty fawn" is showing up on the right.

In my group I have a new desktop that allows remote login by several different users.  So it is acting like a server. I am the only one with sudo access. I also have a samba nas server with tons of storage where each user has their own account/folder and there is one shared account. Since I administer both computers, I have access to all the passwords and folders on the nas and on the desktop and can configure things. 

I can mount the nas server form my account without any problems.

I would like to set the desktop up so that when a user logs on to the desktop, the corresponding folder from the nas is also mounted (and ideally the shared folder as well).  That way, the nas server will just look like another folder in their home directory and so accessing it will be straightforward from a user's point of view.  It is practically important for the nas folder to be mounted as a folder in a specific, consistent location that the user has access to so that they can rely on its location in scripts and programs.

One question:

1) How can I set this up? I'd appreciate some detailed directions.  I can follow the instructions for using /etc/fstab to automatically mount things, but in this case I want to customize mounting for each individual non-administrator user, and so I'm stymied.

Thanks for any help

---

### Post by TheFu on 2018-09-29
If you use NFS, not CIFS, then normal Unix groups and permissions can be used.

I wouldn't mount any external storage directly to any end-user's HOME. Instead, I'd mount that storage somewhere else, perhaps under /data/{user} and /data/{group} then use symbolic links in their HOME or on their DESKTOP to those other locations.  Be certain to setup the share group storage following normal shared storage permissions to force the proper group and group write permissions recursively, automatically.

I have no idea how to accomplish this using CIFS mounts, though I suspect you could use the "force user" option. That always seemed like a hack to me.

Of course, if you have Windows desktops involved, you probably still want CIFS to be available in addition to NFS.

---

