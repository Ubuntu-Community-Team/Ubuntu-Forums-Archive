---
title: "problem doing sshfs mount with public key authentication"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by sambatyon on 2008-06-14
Hi,
 
I'm having trouble mounting over sshfs with public key authentication instead of password authentication (need this to do an automount).
 
I managed to get ordinary ssh logins to not require a password:
 
sambatyon@machina ~ $ ssh sambatyon@filer
sambatyon@filer ~ $
 
However, when I try mounting with sshfs I get the following:
 
sambatyon@machina ~ $ sudo sshfs sambatyon@filer:/shares/internal/backup /mnt/backup -o PasswordAuthentication=no
read: Connection reset by peer
 
I ran strace and got the following (relevant text only):
 
socketpair(PF_FILE, SOCK_STREAM, 0, [3, 4]) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7d766f8) = 10137
 --- SIGCHLD (Child exited) @ 0 (0) ---
waitpid(10137, NULL, 0) = 10137
close(4) = 0
writev(3, [{"\0\0\0\5\1\0\0\0\3", 9}], 1) = 9
read(3, 0x80540d0, 9) = -1 ECONNRESET (Connection reset by peer)
dup(2) = 4
fcntl64(4, F_GETFL) = 0x2 (flags O_RDWR)
fstat64(4, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 3), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fcc000
_llseek(4, 0, 0xbfcce6b8, SEEK_CUR) = -1 ESPIPE (Illegal seek)
write(4, "read: Connection reset by peer\n", 31read: Connection reset by peer
 ) = 31
close(4) = 0
munmap(0xb7fcc000, 4096) = 0
exit_group(1) = ?
Process 10136 detached
 

Any ideas?

---

### Post by hugo_laffez on 2008-06-21
I have the same problem! I could not find anything about this online. Let me know if you are able to solve it!

---

### Post by bgturk on 2009-05-22
I am experiencing the same problem. Have you resolved this issue?

---

### Post by bgturk on 2009-05-22
The problem in my case was that I was storing my private key as:
~/.ssh/identity

Apparently, unlike ssh, sshfs doesn't know that it has to look for it (it looks for id_rsa and id_dsa), so you have to tell it explicitly by uncommenting this line in /etc/ssh/ssh_config:

```
#   IdentityFile ~/.ssh/identity
```

After that, it will be able to log in. 

sshfs is really bad in telling you what the error is. Rather than emitting the mysterious error of remote host resetting the connection, it should have said that the problem lies in the identity file. 

I hard to run it with all these options 
```
sshfs -odebug,sshfs_debug,loglevel=debug

```
to discover where the problem lied.

---

### Post by Alexqw on 2011-03-14
Sorry to reply to such an old thread, but I found the solution and figured it was worth sharing.
```
sshfs -o ssh_command="ssh -i ~/ssh_keys/smckey.pem" username@host.connecting.to.com:/var/www/ ~/mnt/host_mount/
```
Any option you want to pass to ssh can be passed to the "-o ssh_command=" option.

---Alex

---

### Post by stunted on 2011-11-23
You can do it with

```
sshfs -o IdentityFile=~/ssh_keys/smckey.pem username@host.connecting.to.com:/var/www/ ~/mnt/host_mount/
```

Or I tend to fix the uid & gid so they're the same as my local user

```
sshfs -o uid=1042,gid=1042,IdentityFile=~/ssh_keys/smckey.pem username@host.connecting.to.com:/var/www/ ~/mnt/host_mount/
```

---

