---
title: "NIS, NFS and AutoFS"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by davejohnston on 2006-11-10
Hi,

I've just done a fresh install of ubuntu edgy.  I'm trying to setup my system to use NIS to authenticate users and automount NFS shares.

After setting up NIS I was able to confirm it worked by logging in using one of the users specified in the NIS server.
But the automount does not seem to work.

I did:-
/etc/init.d/autofs status
Configured Mount Points:
------------------------
/usr/sbin/automount --timeout=300 /support yp auto_support
/usr/sbin/automount --timeout=300 /project yp auto_project
/usr/sbin/automount --timeout=300 /product yp auto_product
/usr/sbin/automount --timeout=300 /users yp auto_users
/usr/sbin/automount --timeout=300 /dpg yp auto_dpg

Active Mount Points:
--------------------


As you can see it seems to have configured the mounts using NIS, but there are no active mount points.  I can manually mount the nfs shares using the mount command.  

Does anyone know whats wrong???

---

### Post by thk on 2006-11-10
I assume you tried eg "cd /support" and then checked for mounts?

---

### Post by davejohnston on 2006-11-11
Yes I did, but still no active mounts.

I'm a little puzzeled by this, but no one seems to know the anwser.

---

### Post by Tore Van Grembergen on 2006-12-02
I don't know if it helps, but i have NIS,NFS and automount running for quit some time know.
Is use the autofs for mounting the home directory of the users.

The home directory is located on the server (Dapper Drake)
The clients are Edgy Eft

my auto.master file looks like this

#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc  /etc/auto.misc --timeout=60
#/smb   /etc/auto.smb
#/misc  /etc/auto.misc
#/net   /etc/auto.net
/home           auto.home       -rw

my auto.home file looks this

*       DB001.LANDSDIJK.NET:/home/&

Kind regards

Tore

---

### Post by the_original_billq on 2007-05-04
You may want to also check /etc/nsswitch.conf.  If you put an entry in that looks like:

automount:         nis


You can make automount NIS maps called auto.master and auto.home.  Autofs will no longer
look for entries in /etc on the local machine, but will consult the auto.master map.  If you make
the map look like

/home auto.home

It will use the auto.home NIS map for home directory mounts.

You can also point nsswitch.conf to local files by using

automount:         files

In this case, you would have two files in /etc,  one called auto.master that contains

/home           /etc/auto.home

and the other called auto.home that contains

*   your_nfs_server_name:/home/&

(The ampersand matches every user name, using the asterix wildcard as the username match)

This is the tip of the iceberg.  There are a multitude of additional configuration options that can be employed to share data and information via NIS, NFS, & automount.  Sun's website has exhaustive documentation on how to get it all playing nice, and most of this works on Ubuntu/Linux as well.

HTH,
Bill

---

### Post by ethoms on 2008-01-10
I had same problem, autofs would find nis maps but nothing in Active mount points. My solaris server was providing nis automounts to solaris 10 and opensolaris clients no problem, therefore I never thought it was a server-side issue. Then I started to wonder again, why does auto_master suddenly become auto.master, likewise with auto_home becoming auto.home. It seems there is a backward compatability issue with older versions of solaris. Linux must use the newer convention only, strictly. I changed the auto_master to auto.master, likewise with auto_home, also changed the contents of auto.master so that auto_home is now auto.home and auto_direct is now auto.direct. IT WORKS WITH LINUX NOW!

Solution:
1.) Change the nis map source files 'auto_master', 'auto_home', 'auto_direct' to 'auto.master', 'auto.home', 'auto.direct'. Within each of those files change auto_* references to auto.*

2.) Change the Makfile in /var/yp (or wherever your nis maps are built)  to reference auto.* instead of auto_*

Conclussion:
Why the hell did they have to change a "_" for a "." !!!

---

