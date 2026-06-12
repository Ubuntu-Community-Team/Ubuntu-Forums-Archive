---
title: "nfs problem /export/users"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by dagring on 2014-10-05
Hi,

I have had a lot of fun with mounted shares, but after I upgraded to the last kernel. I get the message during boot: problem occured when mounting /export/users. I can mount the share on my client machine, but the boot stops (on the server) with this error message. I get an option to opt out of the problem, or fix it manually. I have looked into fstab and the line:

/home/users    /export/users   none    bind  0  0 

This relates to this message. I don't want to mess with this before I know what I'm doing. Should it be commented out, since it's not working, or what? Another thing is that the /home/users does not exist. This makes my head flying out the window (instead of fixing the problem). Can anybody share some clarity oin this problem?

Dag R

---

### Post by TheFu on 2014-10-05
It is best when sharing a HOME to ensure that it is mounted in exactly the same location on all systems and make the HOME setting match in whatever password file solution you are using (NIS, LDAP) to keep these synchronized. I've never used "bind" mounts for that. I would just change where /home gets mounted in the fstab on the source machine.

---

### Post by dagring on 2014-10-09
I have commented out this line in fstab, and now the source machine seems to restart just fine. I haven't tested it fully yet, but it seems ok. I have also mounted the share on the client machine. Can you tell me why I need to have this line in fstab? Second, I used the official Ubuntu howto NFS, and from this guide I scissored:

"For easier maintenance we will isolate all NFS exports in single directory, where the real directories will be mounted with the --bind option.

    Let's say we want to export our users' home directories in /home/users. First we create the export filesystem:

    # mkdir -p /export/users 

    It's important that /export and /export/users have 777 permissions as we will be accessing the NFS share from the client without LDAP/NIS authentication. This will not apply if using authentication (see below). Now mount the real users directory with:

    # mount --bind /home/users /export/users

    To save us from retyping this after every reboot we add the following

    line to /etc/fstab

    /home/users    /export/users   none    bind  0  0"

How do you understand this in connection to your advice to me?

Dag R

---

### Post by TheFu on 2014-10-09
Yes, I understand it. I find it overly complex and unnecessary.

On the storage machine, mount the storage partition for HOME directly to /exports/home .... if that is where you want them on all machines.  Then export that for NFS use.

Any instructions that suggest 777 permissions are required - they are just wrong/lazy - IMHO. If you understand file permissions, whatever your system needs can be provided. Though in some really strange situations, a bind-mount or ACLs may be necessary, I've never needed those in 20+ yrs.

On the client machines, mount the NFS storage to /exports ... using autofs.  Seem much easier to me than having an extra bind-mount.

---

