---
title: "Kopete troubles"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by Falc7 on 2010-04-20
I am having some trouble getting Kopete to work.
When it starts akondi it gives me some error messages about akondi control process not being registered at dbus, but kopete starts anyway. I added my QQ account, but it dosen't seem to connect as i never get my friends list coming up. There is a yellow exclamation mark next to my account as well, but no explanation as to what this explanation mark means. Can anyone help?

---

### Post by mgranet on 2010-04-20
This thread might be useful:

[http://kubuntuforums.net/forums/index.php?topic=3110072.0]("http://kubuntuforums.net/forums/index.php?topic=3110072.0")

---

### Post by Falc7 on 2010-04-20
Here is the error report:
```


Test 4:  ERROR
--------

MySQL server log contains errors.
Details: The MySQL server error log file &apos;<a href='/home/jamie/.local/share/akonadi/db_data/mysql.err'>/home/jamie/.local/share/akonadi/db_data/mysql.err</a>&apos; contains errors.

File content of '/home/jamie/.local/share/akonadi/db_data/mysql.err':
100421 11:08:33 [Note] Plugin 'FEDERATED' is disabled.
InnoDB: No valid checkpoint found.
InnoDB: If this error appears when you are creating an InnoDB database,
InnoDB: the problem may be that during an earlier attempt you managed
InnoDB: to create the InnoDB data files, but log file creation failed.
InnoDB: If that is the case, please refer to
InnoDB: http://dev.mysql.com/doc/refman/5.1/en/error-creating-innodb.html
100421 11:08:33 [ERROR] Plugin 'InnoDB' init function returned error.
100421 11:08:33 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
100421 11:08:33 [ERROR] Unknown/unsupported table type: innodb
100421 11:08:33 [ERROR] Aborting

100421 11:08:33 [Warning] Forcing shutdown of 1 plugins
100421 11:08:33 [Note] /usr/sbin/mysqld-akonadi: Shutdown complete




Test 9:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 10:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  ERROR
--------

Nepomuk search service not registered at D-Bus.
Details: The Nepomuk search service is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 12:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 13:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share'

Test 14:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server did report error during startup into <a href='/home/jamie/.local/share/akonadi/akonadiserver.error'>/home/jamie/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/jamie/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/jamie/.local/share/akonadi//mysql.conf", "--datadir=/home/jamie/.local/share/akonadi/db_data/", "--socket=/home/jamie/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40b379]
1: akonadiserver [0x40b8c2]
2: /lib/libc.so.6 [0x7fd4a24e6530]
3: /lib/libc.so.6(gsignal+0x35) [0x7fd4a24e64b5]
4: /lib/libc.so.6(abort+0x180) [0x7fd4a24e9f50]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7fd4a36b1864]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40c9e8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x78) [0x7fd4a3740ae8]
8: /usr/lib/libQtCore.so.4 [0x7fd4a37525e9]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7fd4a37537e9]
10: akonadiserver(_ZN6QDebugD1Ev+0x4e) [0x406fee]
11: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer25startMysqlDatabaseProcessEv+0x183b) [0x7fd4a3b2123b]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x2e0) [0x7fd4a3b25d10]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x76) [0x7fd4a3b25fd6]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7fd4a3b272fa]
15: akonadiserver(main+0x3b8) [0x406618]
16: /lib/libc.so.6(__libc_start_main+0xfd) [0x7fd4a24d1abd]
17: akonadiserver [0x406169]
]
" 


Test 15:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/home/jamie/.local/share/akonadi/akonadiserver.error.old'>/home/jamie/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/jamie/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/jamie/.local/share/akonadi//mysql.conf", "--datadir=/home/jamie/.local/share/akonadi/db_data/", "--socket=/home/jamie/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40b379]
1: akonadiserver [0x40b8c2]
2: /lib/libc.so.6 [0x7f42689ff530]
3: /lib/libc.so.6(gsignal+0x35) [0x7f42689ff4b5]
4: /lib/libc.so.6(abort+0x180) [0x7f4268a02f50]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7f4269bca864]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40c9e8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x78) [0x7f4269c59ae8]
8: /usr/lib/libQtCore.so.4 [0x7f4269c6b5e9]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f4269c6c7e9]
10: akonadiserver(_ZN6QDebugD1Ev+0x4e) [0x406fee]
11: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer25startMysqlDatabaseProcessEv+0x183b) [0x7f426a03a23b]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x2e0) [0x7f426a03ed10]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x76) [0x7f426a03efd6]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7f426a0402fa]
15: akonadiserver(main+0x3b8) [0x406618]
16: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f42689eaabd]
17: akonadiserver [0x406169]
]
" 

```

I did this on that page you showed me:
```
You will also experience this problem if you are running an encrypted home directory using encryptfs combined with AppArmor as the Akonadi apparmor profile currently does not account for an ecrypted home (common with Ubuntu Jaunty users). Error messages with include:

    * dmesg produces: 

     ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-13]
     ecryptfs_create: Failed to create file inlower filesystem

    * Akonadi will list the following errors: 

     Akonadi server process not registered at D-Bus

The fix is to edit the following file "/etc/apparmor.d/usr.sbin.mysqld-akonadi". Below the line:

      @{HOME}/.local/share/akonadi/** rwk,

Add a new line:

      @{HOME}/.Private/** rwk,

Restart apparmor and restart akonadi. 
```

and this:
```
Some distributions using Apparmor have it set up in a way that prevents Akonadi from running its internal database server. This can result in a variety of fuzzy error messages, including but not limited to the following:

    * unknown error 255 when running akonadictl
    * "DB error: 'Could not open required defaults file: /home/$username/.local/share/akonadi/mysql.conf" 

You can solve this by running aa-complain mysqld with root privileges then reload apparmor. On KUbuntu this is:

sudo aa-complain mysqld
sudo /etc/init.d/apparmor reload

```

But still no luck. I am going to keep investigating

---

