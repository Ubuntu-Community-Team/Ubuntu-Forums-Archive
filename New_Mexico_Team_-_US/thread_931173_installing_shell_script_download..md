---
title: "installing shell script download."
date: 2008-09-27
forum: New Mexico Team - US
---

### Post by randancing on 2008-09-27
I downloaded this thing from zimbra after reading that Ubuntu has partnered with the company and is offering it. It sits on my desktop like this:



/home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh








 I went to the synaptic manager and tried all of the download categories to no avail. Then I downloaded it from the zimbra website to my desktop. 

Now I have no idea how to get it installed on my computer or to run the thing. I have tried most of the things that I could figure out from the 'help' man, (see the printout below)  and I got nothing.

Does any one know how to get this thing to install and run on Ubuntu. I have read (skimmed, as I don't want to spend the rest of the year trying to figure out what I need)three different tutorials  and I can't find any notation of how to save and run something like this. 

Any help would be appreciated.

james@james-desktop:~$ /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
bash: /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh: Permission denied
james@james-desktop:~$ sudo /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
sudo: /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh: command not found
james@james-desktop:~$ 
james@james-desktop:~$ sudo /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
sudo: /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh: command not found
james@james-desktop:~$ install /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
install: missing destination file operand after `/home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh'
Try `install --help' for more information.
james@james-desktop:~$ install /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh -t/home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh


install: option requires an argument -- t
Try `install --help' for more information.
james@james-desktop:~$ install /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh --t
install: option `--t' requires an argument
Try `install --help' for more information.
james@james-desktop:~$ install --help
Usage: install [OPTION]... [-T] SOURCE DEST
  or:  install [OPTION]... SOURCE... DIRECTORY
  or:  install [OPTION]... -t DIRECTORY SOURCE...
  or:  install [OPTION]... -d DIRECTORY...
In the first three forms, copy SOURCE to DEST or multiple SOURCE(s) to
the existing DIRECTORY, while setting permission modes and owner/group.
In the 4th form, create all components of the given DIRECTORY(ies).

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL] make a backup of each existing destination file
  -b                  like --backup but does not accept an argument
  -c                  (ignored)
  -d, --directory     treat all arguments as directory names; create all
                        components of the specified directories
  -D                  create all leading components of DEST except the last,
                        then copy SOURCE to DEST
  -g, --group=GROUP   set group ownership, instead of process' current group
  -m, --mode=MODE     set permission mode (as in chmod), instead of rwxr-xr-x
  -o, --owner=OWNER   set ownership (super-user only)
  -p, --preserve-timestamps   apply access/modification times of SOURCE files
                        to corresponding destination files
  -s, --strip         strip symbol tables
  -S, --suffix=SUFFIX override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory  treat DEST as a normal file
  -v, --verbose       print the name of each directory as it is created
  -P, --preserve_context (SELinux) Preserve security context
  -Z, --context=CONTEXT  (SELinux) Set security context of files and directories
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
james@james-desktop:~$ install /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh -T
install: missing destination file operand after `/home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh'
Try `install --help' for more information.
james@james-desktop:~$ install /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh --t --mode=MODE
install: accessing `--mode=MODE': No such file or directory
james@james-desktop:~$ install -T /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
install: missing destination file operand after `/home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh'
Try `install --help' for more information.
james@james-desktop:~$

---

### Post by ad_267 on 2008-09-27
```
$ chmod +x /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
$ /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
```

You need the chmod +x to make it executable. Alternatively you can right click on it and select properties - permissions and make it executable there.

---

### Post by randancing on 2008-09-27
Thank you so much. I know these beginners questions must become boring, but after five hours of messing with the thing, it was a blessing to get an answer. Thank you.

jim

---

### Post by ad_267 on 2008-09-27
No problem, it's one of the differences between Windows and Linux that often trips people up. It does make things more secure as you can't run something you've downloaded from the internet unless you give it permission to run.

---

### Post by linux-free on 2011-07-25
Also, you may use the ls command to check and see if a file is executable:
```

ls -l /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
```
[I]
Output:[/I]

rwxrwxrwx
(user)(group)(others)

The output is in a format: rwx (read)(write)(execute)

It is in bit format, 4,2,1


*Example*:

```
chmod 755 /home/james/Desktop/zdesktop_0_90_build_1278_linux_i686.sh
```
chmod 755 would make:

(rwxr-xr-x)





7 = 4,2,1 one bit in each = rwx (for you)
5 = 4,1 = r-x (for your group)
5 = 4,1 = r-x (for all)

---

