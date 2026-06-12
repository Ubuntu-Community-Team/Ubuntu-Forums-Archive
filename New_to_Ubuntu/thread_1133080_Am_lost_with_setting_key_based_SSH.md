---
title: "Am lost with setting key based SSH"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by akkad on 2009-04-22
am following this link ([https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH))
to set rsa keys to be used in ssh connection, where the point i stuck with in this help page is where to execute the following commands:
- ssh-keygen -t rsa
- ssh-copy-id -i ~/.ssh/id_rsa.pub username@host

on my desktop ubuntu which represents the ssh client or on my ubuntu server which represents the ssh server ??

---

### Post by bodhi.zazen on 2009-04-22
The client is the machine you are connecting from (you ubuntu desktop)

The server is the machine you are connecting to (your ubuntu server).

---

### Post by llamabr on 2009-04-22
Here's a howto I always use:

[http://llamakc.org/~ken/ssh-keys.php](http://llamakc.org/~ken/ssh-keys.php)

---

### Post by akkad on 2009-04-22
> **bodhi.zazen said:**
> The client is the machine you are connecting from (you ubuntu desktop)

The server is the machine you are connecting to (your ubuntu server).

i know this, but my problem is where to execute those commands i mentioned on the server or on the client?

---

### Post by altonbr on 2009-04-22
I also have a [SSH/rsync script]("http://ubuntuforums.org/showthread.php?t=639979") that may of be some help :)

---

### Post by bodhi.zazen on 2009-04-22
> **akkad said:**
> i know this, but my problem is where to execute those commands i mentioned on the server or on the client?

client

user@server == server

so 

scp file_on_client   user@server:location_on_server

---

### Post by akkad on 2009-04-23
> **bodhi.zazen said:**
> client

user@server == server

so 

scp file_on_client   user@server:location_on_server

good, but before i start copy files i need to setup the keys, so
"ssh-keygen -t rsa" this should be run on the server or on the client?
also "ssh-copy-id -i ~/.ssh/id_rsa.pub username@host" should be run on the server or on the client?

---

### Post by bodhi.zazen on 2009-04-23
Those commands are being run on the client.

You should be able to tell from the commands you are running.

Again, the server is **user@server**

> ssh-copy-id -i ~/.ssh/id_rsa.pub username@host```
ssh-copy-id -i [COLOR=blue]File on client == ~/.ssh/id_rsa.pub[/COLOR] [COLOR=red]To server == username@host[/COLOR]
```I do not understand where you are missing this concept.

server is ALWAYS identified by user@server

You can drop the user if the user is the same on client and server, in which case you are specifying the server either by host name or ip address, so it really should be obvious.

---

### Post by akkad on 2009-04-23
> **bodhi.zazen said:**
> Those commands are being run on the client.

You should be able to tell from the commands you are running.

Again, the server is **user@server**

```
ssh-copy-id -i [COLOR=blue]File on client == ~/.ssh/id_rsa.pub[/COLOR] [COLOR=red]To server == username@host[/COLOR]
```I do not understand where you are missing this concept.

server is ALWAYS identified by user@server

You can drop the user if the user is the same on client and server, in which case you are specifying the server either by host name or ip address, so it really should be obvious.

in fact i dont know the mechanism of using these rsa keys :confused:
can you explain to me please, the keys generation "ssh-keygen -t rsa" will be done on clients only no need on server? if so then how will the server validate the client key?
one more thing what does the command "ssh-copy-id" do?

---

### Post by bodhi.zazen on 2009-04-23
You can make a key anywhere you like, client, server, does not matter.

When you make a key you can either use the default name, or better give it a name. Let us say me make a key, "foo"

```
ssh-keygen -t rsa -b 4096 -f foo
```This makes 2 files , "foo" and "foo.pub". these tow files are also called a 'key pair"

Now transfer, any way you like. "foo.pub" to the server and "foo" to the client.

Now put the contents of "foo.pub" into /home/user/authorized-keys on the server.

You can do this with the command

```
cat foo.put >> ~/.ssh/authoruzed_keys
```Now use the key from the client

```
ssh -i ~/.ssh/foo user@server
```This works because you put one key on the client (foo) and one on the server (foo.pub) in ~/.ssh/authorized_keys (again on the server) and you know the password for the key pair.

You can automate this from the client with

```
ssh-copy-id -i foo.pub user@server
```That command transfers the key foo.pub to the server and puts it into ~/.ssh/authorized_keys all in 1 step (rather then 3)

Manually you would (from the client) : 

ssh-keygen -t rsa -b 4096 -f foo
scp foo.put user@server
ssh user@server
ssh user@server "cat foo.pub >> .ssh/authorized_keys"

those 4 commands  ^^ are replaced by two commands :

```
[COLOR=green]# Make a key
ssh-keygen -t rsa -b 4096 -f foo[/COLOR]

[COLOR=blue]#Transfer the *pub of the key pair to the server
ssh-copy-id -i foo.pub user@server[/COLOR]

[COLOR=darkred]#Log into server with key
ssh -i ~/.foo user@server[/COLOR]
```

---

### Post by akkad on 2009-04-23
thanks man, now it is totally clear, thanks alot, and sorry for my misunderstanding but the time here in my country is 4am midnight so am half sleepy and half working since 6 hours setting up my ubuntu server :(, thnx anyway.

---

### Post by 11hjpphty76lkjj on 2009-04-27
I wrote this today and am curious on getting feedback.

```
#!/bin/bash
# created by aaron (kalosaurusrex)
# version .02
# 4/27/2009
#
# use case:
# for creating the ssh keyless login keys and configuring both the remote and local system for keyless ssh
#
# to use:
# copy this script to the system you want to login to the remote system from the requires no password prompt
# save file as .sh. (ie keygen.sh)
# chmod +x keygen.sh
# ./keygen.sh
#
# use at own risk
#
LOCAL_USR=`whoami`
read -p "Remote system ssh port (default, 22, if using default enter 22): " VAR_INPUT5
export VAR_REMOTE_PORT="`echo "${VAR_INPUT5}" | tr -cd '[:alnum:] [:space:]'`"
echo ""
read -p "Remote system IP address or hostname: " VAR_INPUT
export VAR_REMOTE="`echo "${VAR_INPUT}"`"
echo ""
read -p "Remote system username: " VAR_INPUT1
export VAR_REMOTE_USR="`echo "${VAR_INPUT1}"`"
echo ""
echo ""
echo "Remote Port: ${VAR_REMOTE_PORT}"
echo "Remote System: ${VAR_REMOTE}"
echo "Remote Username: ${VAR_REMOTE_USR}"
echo ""
echo "This step will create the ssh keys on the remote system: $VAR_REMOTE"
echo ""
echo "NOTE: Be sure to put the full path to the rsa file: /home/$VAR_REMOTE_USR/.ssh/filename_rsa"
echo ""
sleep 5
ssh -p $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE 'ssh-keygen -t rsa'
echo ""
echo "******"
echo "NOTE: At the next prompt enter the FILENAME ONLY from above. IE filename_rsa, etc"
echo "******"
echo ""
read -p "Enter the filename of the key you created above (IE: filename_rsa):" VAR_INPUT2
export VAR_FILENAME="`echo "${VAR_INPUT2}"`"
echo "Filename is: ${VAR_FILENAME}"
echo ""
ssh -p $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE 'cat /home/'$VAR_REMOTE_USR'/.ssh/'$VAR_FILENAME'.pub > /home/'$VAR_REMOTE_USR'/.ssh/authorized_keys'
ssh -p $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE 'chmod 600 /home/'$VAR_REMOTE_USR'/.ssh/authorized_keys'
echo ""
echo ""
echo "Copy keys to the local system.."
scp -P $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE:/home/$VAR_REMOTE_USR/.ssh/$VAR_FILENAME.pub /home/$LOCAL_USR/.ssh/.
scp -P $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE:/home/$VAR_REMOTE_USR/.ssh/$VAR_FILENAME /home/$LOCAL_USR/.ssh/.
cat /home/$LOCAL_USR/.ssh/$VAR_FILENAME.pub >> /home/$LOCAL_USR/.ssh/authorized_keys
cat /home/$LOCAL_USR/.ssh/$VAR_FILENAME >> /home/$LOCAL_USR/.ssh/authorized_keys
chmod 600 /home/$LOCAL_USR/.ssh/authorized_keys
chmod 600 /home/$LOCAL_USR/.ssh/$VAR_FILENAME.pub
echo ""
echo "ssh should now work without a password prompt. try running:"
echo ""
echo "ssh -i /home/$LOCAL_USR/.ssh/$VAR_FILENAME -p $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE"
echo ""
echo "should not be prompted for password."
echo ""
exit 
```

Or download the attached file.

Copy sshkeymkr.sh to the machine you want to login to the remote machine from.

Then 
chmod +x sshkeymkr.sh
./sshkeymkr.sh

Should setup the keys, etc.  Just follow the prompts.

Thoughts/Suggestions?  I'm putting my feet into a little bash scripting. I'm sure there are other ways to do this..but there ya go.

---

### Post by andrew.46 on 2009-05-06
Hi bodhi.zazen,

> **bodhi.zazen said:**
> [...] you put one key on the client (foo) and one on the server (foo.pub) in ~/.ssh/authorized_keys (again on the server) and you know the password for the key pair.

Can I ask your thoughts on the so-called 'password-less SSH login' where the process you describe is carried out but *no passphrase* is entered?

Thanks for your trouble,

Andrew

---

### Post by bodhi.zazen on 2009-05-06
> **andrew.46 said:**
> Hi bodhi.zazen,



Can I ask your thoughts on the so-called 'password-less SSH login' where the process you describe is carried out but *no passphrase* is entered?

Thanks for your trouble,

Andrew

Personally I do not use passwordless keys, if I wish I use ssh-agent.

You can make a key with no password and then use it to log in. I see this as reasonably secure as someone still would need to obtain the key.

I increase security in two ways :

1. Disable password logins.

2. If you use a passwordless key, for say commands (rsync, tunnels, etc) then secure the key a bit by using forced commands.

I do not know a good reference for forced commands, see my tutorial on svn+ssh for an example.

[http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

---

### Post by altonbr on 2009-05-09
> **kalosaurusrex said:**
> I wrote this today and am curious on getting feedback.

```
#!/bin/bash
# created by aaron (kalosaurusrex)
# version .02
# 4/27/2009
#
# use case:
# for creating the ssh keyless login keys and configuring both the remote and local system for keyless ssh
#
# to use:
# copy this script to the system you want to login to the remote system from the requires no password prompt
# save file as .sh. (ie keygen.sh)
# chmod +x keygen.sh
# ./keygen.sh
#
# use at own risk
#
LOCAL_USR=`whoami`
read -p "Remote system ssh port (default, 22, if using default enter 22): " VAR_INPUT5
export VAR_REMOTE_PORT="`echo "${VAR_INPUT5}" | tr -cd '[:alnum:] [:space:]'`"
echo ""
read -p "Remote system IP address or hostname: " VAR_INPUT
export VAR_REMOTE="`echo "${VAR_INPUT}"`"
echo ""
read -p "Remote system username: " VAR_INPUT1
export VAR_REMOTE_USR="`echo "${VAR_INPUT1}"`"
echo ""
echo ""
echo "Remote Port: ${VAR_REMOTE_PORT}"
echo "Remote System: ${VAR_REMOTE}"
echo "Remote Username: ${VAR_REMOTE_USR}"
echo ""
echo "This step will create the ssh keys on the remote system: $VAR_REMOTE"
echo ""
echo "NOTE: Be sure to put the full path to the rsa file: /home/$VAR_REMOTE_USR/.ssh/filename_rsa"
echo ""
sleep 5
ssh -p $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE 'ssh-keygen -t rsa'
echo ""
echo "******"
echo "NOTE: At the next prompt enter the FILENAME ONLY from above. IE filename_rsa, etc"
echo "******"
echo ""
read -p "Enter the filename of the key you created above (IE: filename_rsa):" VAR_INPUT2
export VAR_FILENAME="`echo "${VAR_INPUT2}"`"
echo "Filename is: ${VAR_FILENAME}"
echo ""
ssh -p $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE 'cat /home/'$VAR_REMOTE_USR'/.ssh/'$VAR_FILENAME'.pub > /home/'$VAR_REMOTE_USR'/.ssh/authorized_keys'
ssh -p $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE 'chmod 600 /home/'$VAR_REMOTE_USR'/.ssh/authorized_keys'
echo ""
echo ""
echo "Copy keys to the local system.."
scp -P $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE:/home/$VAR_REMOTE_USR/.ssh/$VAR_FILENAME.pub /home/$LOCAL_USR/.ssh/.
scp -P $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE:/home/$VAR_REMOTE_USR/.ssh/$VAR_FILENAME /home/$LOCAL_USR/.ssh/.
cat /home/$LOCAL_USR/.ssh/$VAR_FILENAME.pub >> /home/$LOCAL_USR/.ssh/authorized_keys
cat /home/$LOCAL_USR/.ssh/$VAR_FILENAME >> /home/$LOCAL_USR/.ssh/authorized_keys
chmod 600 /home/$LOCAL_USR/.ssh/authorized_keys
chmod 600 /home/$LOCAL_USR/.ssh/$VAR_FILENAME.pub
echo ""
echo "ssh should now work without a password prompt. try running:"
echo ""
echo "ssh -i /home/$LOCAL_USR/.ssh/$VAR_FILENAME -p $VAR_REMOTE_PORT $VAR_REMOTE_USR@$VAR_REMOTE"
echo ""
echo "should not be prompted for password."
echo ""
exit 
```

Or download the attached file.

Copy sshkeymkr.sh to the machine you want to login to the remote machine from.

Then 
chmod +x sshkeymkr.sh
./sshkeymkr.sh

Should setup the keys, etc.  Just follow the prompts.

Thoughts/Suggestions?  I'm putting my feet into a little bash scripting. I'm sure there are other ways to do this..but there ya go.

If you want to compare, I wrote this some time ago: [http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

---

