---
title: "SSH tunneling. &quot;bind: Address already in use&quot;"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by Dospanes on 2013-09-17
Dear friends,

I'm very new to Ubuntu and not very firm with the terminal syntax and system settings yet. I hope someone can advice me on two issues regarding SSH and the secure use of scripts in the terminal.

So yesterday I sucessfully set up a ssh tunnel with PuTTY SSH Client defining Source Pourt and Destination under -> SSH ->Tunnels.
And today I tried to do the same but using the build-in SSH client in the terminal. I entered the following syntax:

ssh -f -L 5432:localhost:5433 *someAccountname*@*someIPaddress*  sleep 10
I was prompted to enter a password.
After entering the password the following error message appeared: "bind: Address already in use"

So I guessed that PuTTY was still using the local port. After deinstalling PuTTY the same errormessage came up and after reinstalling PuTTY all configuration was still there. So I guess that PuTTY somehow changes a config file that controls sistemwide port-uses.

So first:Is this right and can I change that file in order to be abled to use the terminal client?

And second: I would like to use the terminal client since this enables me to write a script and avoid annoying clicking and providing logincredentials every time I want to connect to the server. 
So is there a way to safely store the password within a script with the above syntax? If yes how would the syntax look like and how can I safely secure the script from thirdparties? Ithought of maybe encrypting all scripts that contain password information with a master password. Like this I would not need to remember all login-information for the different purposes...

---

### Post by steeldriver on 2013-09-17
Hello and welcome to the forum

As far as I know, putty doesn't do anything like that (however I only use the Windows version) - you can check what process/service is bound to the port using the lsof command e.g.

```
sudo lsof -i :5432
```

For your second question, you should use key-based authentication instead of storing your password.

---

### Post by Lars Noodén on 2013-09-17
For the key-based authentication, you can take advantage of the agent built into Ubuntu to save your passphrase.  If you use that, you will only need to enter your passphrase once per Ubuntu session yet still be able to log into the remote machine when you want.  You can do that with [ssh-add](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh-add.1.html) and a key you have set up for that purpose.

```

ssh-add /home/dospanes/.ssh/some_key_rsa

```

There might also be a way to set that up with seahorse, but I haven't looked.

---

### Post by Dospanes on 2013-09-18
All right. Thank you very much for your advices!
Checking out the port via ```
sudo lsof -i :5432
```
gave me that postgreSQL was using the port. After killing the process I could correctly connect to the servier via SSH tunneling.

Still the main problem was  that I accidently changed the ports in the above. 
```
ssh -f -L 5432:localhost:5433 *someAccountname*@*someIPaddress*  sleep 10
```
where it should have been:
```
ssh -f -L 5433:localhost:5432 *someAccountname*@*someIPaddress*  sleep 10
```
since i tried to connect to the postgreSQL on the server that was running on port 5432.

Some reading in the [Ubuntu Documentation on Port Forwarding]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding") was helpfull. 

I also checked out the information about working with SSH keys and thanks to the [Ubuntu documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") I was abled to set up the connection with the keys. 
Connecting now works correctly entering the following syntax:
```
ssh -L 5433:localhost:5432 *someAccountname*@*someIPaddress*
```

---

### Post by steeldriver on 2013-09-18
Let's take a step back - what exactly are you trying to do? It *sounds* like you are trying to connect remotely to a postgresql server on someHost:5432 (5432 is the default port for postgresql, I think). If that's the case then you probably have your ports the wrong way around i.e. you *probably* want your tunnel to be

```
ssh -L **5433**:localhost:**5432** someuserid@someHostadress
```

in which case you would then connect your local postgresql client to localhost:5433

The -L 'end' of the tunnel can be any free port on the local machine instead of 5433 - it can even be 5432 if there is no postgresql server running locally. You may also need to modify the postgresql user table to allow connections from the external client (although if it's working via putty, it sounds like you have that part covered).

---

### Post by Dospanes on 2013-09-18
yes thats it. I just found that out too just now....thanks for your help!

---

