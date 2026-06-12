---
title: "Passphraseless SSH - Created Key but still requesting password"
date: 2016-10-13
forum: Networking &amp; Wireless
---

### Post by drhoffma on 2016-10-13
Dear Ubuntu Community,

I'm running Ubuntu 16.04.  I'm trying to set up Passphraseless SSH to work with Hadoop.

Here are the instructions I'm following:

Install openssh:

```
$ sudo apt-get install openssh-server
```

Then try to ssh into your localhost:

```
$ ssh localhost
```

If you get an error similar to Permission denied (publickey)  (which under most circumstances you should, unless you have previously set up passphraseless SSH), you’ll need to execute the following commands to generate your RSA key:
```

$ ssh-keygen -t dsa -P '' -f ~/.ssh/id_dsa
$ cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys
```

You should now be able to SSH into your machine from a local shell without a passphrase:
```

$ ssh localhost
```


However after following the instructions to generate the keys, my system still requires a password.  I then followed this guide: [http://linoxide.com/ubuntu-how-to/setup-passwordless-ssh-logon-ubuntu-14-04/](http://linoxide.com/ubuntu-how-to/setup-passwordless-ssh-logon-ubuntu-14-04/)  And edited /etc/ssh/sshd.config as instructed.  I changed a line:
  
```
PermitRootLogin without-password
```

changed above line from "prohibit-password"

However someone on another forum ([community.pyimagesearch.com]("http://community.pyimagesearch.com")) said that I shouldn't have to change any settings in sshd.config.

Does anyone have any suggestions for me?

Thank you,
David

---

### Post by SeijiSensei on 2016-10-13
Run "ssh -v" or "ssh -vv" and see what it reports.

---

### Post by drhoffma on 2016-10-15
Thanks for your help, [[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195").

```
drhoffma@drhoffma-ThinkPad-T500:~$ ssh -v
usage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file] [-L address]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-Q query_option] [-R address] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] [user@]hostname [command]
drhoffma@drhoffma-ThinkPad-T500:~$ ssh -vv
usage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file] [-L address]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-Q query_option] [-R address] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] [user@]hostname [command]
drhoffma@drhoffma-ThinkPad-T500:~$ ssh -V
OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
drhoffma@drhoffma-ThinkPad-T500:~$ ssh -VV
OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
drhoffma@drhoffma-ThinkPad-T500:~$ 
```

---

### Post by deadflowr on 2016-10-15
I think it was meant to run it with the -v, -vv in the used ssh string, like:
```
ssh -v user@remote-machine-address
```

---

### Post by frostschutz on 2016-10-16
SSH is picky regarding permissions. Check output of 

```

$ ls -ld ~ ~/.ssh ~/.ssh/authorized_keys
drwx------ user:user /home/user
drwx------ user:user /home/user/.ssh
-rw------- user:user /home/user/.ssh/authorized_keys

```

If it's -rw-rw-rw or some other such thing, SSH will ignore it.

If your permissions are wrong you can fix them like thus: (at your own risk)

```

chmod 700 ~ ~/.ssh
chmod 600 ~/.ssh/authorized_keys
chown user:user ~ ~/.ssh ~/.ssh/authorized_keys

```

---

### Post by SeijiSensei on 2016-10-16
> **drhoffma said:**
> Thanks for your help, SeijiSensei

If you're new to *nix systems, all commands are case-sensitive.  You can read the "manual page" for any command by typing "man program_name" at the prompt, e.g., "man ssh".  You'll see that the "-v" switch stands for "verbose"; this is a common feature of many command-line programs.  Some programs like ssh allow you to use two or even "v's" to increase the degree of verbosity.  In contrast the capitalized "-V" switch often prints information about the version of the program being used.

In this case, I suggested using "ssh -v" as in "ssh -v user@server" to have the command display the steps it is taking to make the connection.  That should give you some insight into where the problems lay.

---

