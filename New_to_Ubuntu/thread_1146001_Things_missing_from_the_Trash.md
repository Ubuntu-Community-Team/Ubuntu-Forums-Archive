---
title: "Things missing from the Trash"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by omkarwagh on 2009-05-02
Hi

I have two partitions one for the root and one for my home directory. 

Recently I ran out of space on the root partition. I read that a large part of this is due to the .deb files that are cached in /var/cache/apt/archives. So I went there and sure enough there was nearly 1.6 GB being wasted right there. 

I then selected all the files and pressed the "Del" key. After that it took quite some time to move everything to the "Trash". However, when I open the trash now, it says "Sorry, could not display all the contents of "trash": Operation not supported".

My root partition still shows 0 bytes free and I have no way of accessing these 1.6GB now since I can't find them aywhere.

Any help?
Thanks in advance.

---

### Post by sahabcse on 2009-05-02
Past the o/p of 

#df -h

#sudo du -csh ./*

---

### Post by omkarwagh on 2009-05-02
o/p of df -h:-
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              11G   11G     0 100% /
tmpfs                 498M     0  498M   0% /lib/init/rw
varrun                498M  336K  497M   1% /var/run
varlock               498M     0  498M   0% /var/lock
udev                  498M  160K  498M   1% /dev
tmpfs                 498M   76K  498M   1% /dev/shm
lrm                   498M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2             748M  151M  559M  22% /boot
/dev/sda5              96G   65G   29G  70% /home
overflow              1.0M 1020K  4.0K 100% /tmp
/home/omkarwagh/.Private
                       96G   65G   29G  70% /home/omkarwagh/Private

sudo du -csh ./*:-
sudo du -csh ./*
4.0K	./Desktop
4.0K	./eagle
8.0K	total

---

### Post by sahabcse on 2009-05-02
Paste the following also
#cd /
#du -csh ./*

---

### Post by omkarwagh on 2009-05-02
here it is:-
sudo du -csh ./*
6.1M	./bin
135M	./boot
0	./cdrom
236K	./dev
20M	./etc
du: cannot access `./home/omkarwagh/.gvfs': Permission denied
64G	./home
4.0K	./initrd
0	./initrd.img
0	./initrd.img.old
1.3G	./lib
16K	./lost+found
16K	./media
4.0K	./mnt
du: cannot access `./proc/5336/task/5336/fd/4': No such file or directory
du: cannot access `./proc/5336/task/5336/fdinfo/4': No such file or directory
du: cannot access `./proc/5336/fd/4': No such file or directory
du: cannot access `./proc/5336/fdinfo/4': No such file or directory
0	./proc
1.7G	./root
8.1M	./sbin
4.0K	./selinux
4.0K	./srv
0	./sys
1020K	./tmp
7.1G	./usr
327M	./var
0	./vmlinuz
0	./vmlinuz.old
75G	total

my suspicion:- 1.7G on ./root? i rarely use the root account. i think that's where they've gone.

---

### Post by sahabcse on 2009-05-02
so double check the /root folder using du -csh ./* command.

cd /root
#du -csh ./* 

If there unnecessary files. Try to remove it from there.

---

### Post by omkarwagh on 2009-05-02
ok i think i got them.

they were in /root/.local/share/Trash

I still have a few questions though:-
1.isn't the root account's working directory /home/root? so when is /root used and when is /home/root used?
2.isn't the trash directory ~/.Trash? at least it used to be on some older version of ubuntu. i'm guessing it's been changed now to ~/.local/share/Trash
3.any reasons as to why i couldn't see this in the trash using nautilus?

thanks to sahabcse

---

### Post by sahabcse on 2009-05-02
good to hear you the issue is solved. Ans Given below for your doubt

1.isn't the root account's working directory /home/root? so when is /root used and when is /home/root used?

Ans:
       
The /root directory is the home directory of the root account (Admin). It is also referred to as the root user's home directory (and not as the root directory). 

The root account (which is also referred to as the root user, the administrative user, the system administrator, the superuser or just root) is the user name or account that has access to all commands and files on a Unix-like operating system.

/ is a standard first-tier directory in the root directory (as are /bin, /boot, /dev, /etc, /home, /mnt, /sbin and /usr). The root directory is the top level directory on any Unix-like operating system, 

If you log by root user account you can see the trash folder using nautilus.

---

### Post by antony.s on 2009-05-02
> **omkarwagh said:**
> 2.isn't the trash directory ~/.Trash? at least it used to be on some older version of ubuntu. i'm guessing it's been changed now to ~/.local/share/Trash
3.any reasons as to why i couldn't see this in the trash using nautilus?

thanks to sahabcse

2. When you were deleting the files in /var/cache/apt/archives you would have been working as root (you deleted using the sudo command, right?), so the files went to the trash folder for root

3. When you were looking at ~/.Trash you were looking at the Trash folder of your account, not root's

---

