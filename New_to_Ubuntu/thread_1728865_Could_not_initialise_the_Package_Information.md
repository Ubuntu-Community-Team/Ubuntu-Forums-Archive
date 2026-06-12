---
title: "Could not initialise the Package Information"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by cressrt on 2011-04-14
I have a "Stop Sign" error message occurred and could not find this within current posts; the error is:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


This also occurs when trying to run the Package Manager and the Software Centre will not open.
Any help would be appreciated.

---

### Post by TeoBigusGeekus on 2011-04-14
Rename the lists directory
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists_old
```
clean up the apt cache
```
sudo apt-get clean
```
and try again.

---

### Post by cressrt on 2011-04-14
OK that has worked, but not totally. The Stop sign is still there, the Update Manager, Package Manager and Software Centre all open; however when I check for update the following error occurs:

An unhandled error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

With Details of:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 778, in simulate
    lock.lists_lock.acquire()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/lock.py", line 66, in acquire
    process = get_locking_process_name(self.path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/lock.py", line 83, in get_locking_process_name
    with open(lock_path,"r") as fd_lock_read:
IOError: [Errno 2] No such file or directory: '/var/lib/apt/lists/lock'

?

---

