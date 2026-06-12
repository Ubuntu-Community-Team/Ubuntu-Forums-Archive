---
title: "how to connect to sftp server"
date: 2019-03-29
forum: Networking &amp; Wireless
---

### Post by matt18 on 2019-03-29
Ok, in an older version of ubuntu i was running, there was the file>connect to option in gnome. clicking this would open up a new window where i could pick ssh, port number host etc. 

i can not find that now. 

Also, i have generated my keys with ssh-keygen. The keys work, i have tested it from a windows machine and from ubuntu using filezilla.

now i want to connect via the filemanager but not sure how.

I have added the ssh-add /home/matt/.ssh/<keyname> in autostartup. Is there anymore i have to do for the key? was this the best way?

Thanks

---

### Post by #&amp;thj^% on 2019-03-29
Instead of filling this post up with a lot of text, have a look here: [https://linuxconfig.org/how-to-setup-sftp-server-on-ubuntu-18-04-bionic-beaver-with-vsftpd](https://linuxconfig.org/how-to-setup-sftp-server-on-ubuntu-18-04-bionic-beaver-with-vsftpd)
If you need more help just post back.

---

### Post by matt18 on 2019-03-29
> **1fallen said:**
> Instead of filling this post up with a lot of text, have a look here: [https://linuxconfig.org/how-to-setup-sftp-server-on-ubuntu-18-04-bionic-beaver-with-vsftpd](https://linuxconfig.org/how-to-setup-sftp-server-on-ubuntu-18-04-bionic-beaver-with-vsftpd)
If you need more help just post back.

Thank you for the tutorial:)

The server is up and running on my win10 box using bitvise ssh. I can sftp into the server from my phone, tablet, MXlinux, win10 and xp, but for some reason ubuntu 18.04 is having an issue. I do not know where to put the RSA private key for ubuntu.

i have it stored in the /home.ssh folder

but i dont know how to have ubuntu read said key. Everytime i try to do sftp://IP:8022. i get access is denied. it never asks for username. i have also tried sftp://USERNAME@IP:8022 with same error

I have the following in the autostartup:

ssh-add /home/.ssh/id_rsa

But still no go. access denied

---

### Post by #&amp;thj^% on 2019-03-29
You definitively set yours up differently than i do.
Post back this:
```
cat /etc/ssh/sshd_config
```
Works even on 19.04:
```
$ sftp mefiles@localhost
mefiles@localhost's password: 
Connected to mefiles@localhost.
sftp> ls
uploads 
```  
Mine looks like:
```
Match User mefiles
ForceCommand internal-sftp
PasswordAuthentication yes
ChrootDirectory /var/sftp
PermitTunnel no
AllowAgentForwarding no
AllowTcpForwarding no
X11Forwarding no

```
Here's what each of those directives do:
[list]
   [*]Match User tells the SSH server to apply the following commands only to the user specified. Here, we specify mefiles.
    [*]ForceCommand internal-sftp forces the SSH server to run the SFTP server upon login, disallowing shell access.
   [*] PasswordAuthentication yes allows password authentication for this user.
   [*] ChrootDirectory /var/sftp/ ensures that the user will not be allowed access to anything beyond the /var/sftp directory.
   [*] AllowAgentForwarding no, AllowTcpForwarding no. and X11Forwarding no disables port forwarding, tunneling and X11 forwarding for this user.[/list]

This set of commands, starting with Match User, can be copied and repeated for different users too. Make sure to modify the username in the Match User line accordingly.
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Disco Dingo (development branch)
Release:	19.04
Codename:	disco

```

---

### Post by matt18 on 2019-03-29
matt@Ubuntu18:~$ cat /etc/ssh/sshd_config
cat: /etc/ssh/sshd_config: No such file or directory

which makes sense because ubuntu is not my ssh server. Windows 10PC at home is the ssh server. i am just trying to connect to it:)

--
$ sftp mefiles@localhost
mefiles@localhost's password: 
Connected to mefiles@localhost.
sftp> ls
uploads
----------

So on my server, i have disabled passwords. I am wanting to use keys only. I have keys on my phone, tablet, winxp, win10LAPTOP and they connect fine to the server. But i can not get ubuntu 
to connect to the win10 ssh server because i do not know where the rsa key is supposed to be. I know on other distros, putting it in the .ssh folder is the right place.

Every documentation i read about keys talks about how to setup the ubuntu ssh server,use the copy-id command to put the rsa key ON the server, which i am NOT doing. I am using ubuntu as the host:)

---

### Post by #&amp;thj^% on 2019-03-29
You may use keys that's prefectly normal, but where did you place them?
someone else may be more suited to this post then, I just don't use windows period and haven't for several years now.
**But as an example only:  **
```
ssh-copy-id username@remote_host
```

You may see the following message:
```

Output
The authenticity of host '203.0.113.1 (203.0.113.1)' can't be established.
ECDSA key fingerprint is fd:fd:d4:f9:77:fe:73:84:e1:55:00:ad:d6:6d:22:fe.
Are you sure you want to continue connecting (yes/no)? yes
```

This means that your local computer does not recognize the remote host. This will happen the first time you connect to a new host. Type "yes" and press ENTER to continue.

Next, the utility will scan your local account for the id_rsa.pub key that you created earlier. When it finds the key, it will prompt you for the password of the remote user's account:
```

Output
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
username@203.0.113.1's password:
```

Type in the password (your typing will not be displayed for security purposes) and press ENTER. The utility will connect to the account on the remote host using the password you provided. It will then copy the contents of your ~/.ssh/id_rsa.pub key into a file in the remote account's home ~/.ssh directory called authorized_keys.

You should see the following output:
```

Output
Number of key(s) added: 1
```

Now try logging into the machine, with:   "ssh 'username@203.0.113.1'"
and check to make sure that only the key(s) you wanted were added.

At this point, your id_rsa.pub key has been uploaded to the remote account. 

Copying Public Key Using SSH

If you do not have ssh-copy-id available, but you have password-based SSH access to an account on your server, you can upload your keys using a conventional SSH method.

We can do this by using the cat command to read the contents of the public SSH key on our local computer and piping that through an SSH connection to the remote server.

On the other side, we can make sure that the ~/.ssh directory exists and has the correct permissions under the account we&#8217;re using.

We can then output the content we piped over into a file called authorized_keys within this directory. We&#8217;ll use the >> redirect symbol to append the content instead of overwriting it. This will let us add keys without destroying previously added keys.

The full command looks like this:

```
cat ~/.ssh/id_rsa.pub | ssh username@remote_host "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

You may see the following message:
```

Output
The authenticity of host '203.0.113.1 (203.0.113.1)' can't be established.
ECDSA key fingerprint is fd:fd:d4:f9:77:fe:73:84:e1:55:00:ad:d6:6d:22:fe.
Are you sure you want to continue connecting (yes/no)? yes
```

This means that your local computer does not recognize the remote host. This will happen the first time you connect to a new host. Type "yes" and press ENTER to continue.

Afterwards, you should be prompted to enter the remote user account password:
```

Output
username@203.0.113.1's password:
```

After entering your password, the content of your id_rsa.pub key will be copied to the end of the authorized_keys file of the remote user's account. Continue on to Step 3 if this was successful.
Copying Public Key Manually

If you do not have password-based SSH access to your server available, you will have to complete the above process manually.

We will manually append the content of your id_rsa.pub file to the ~/.ssh/authorized_keys file on your remote machine.

To display the content of your id_rsa.pub key, type this into your local computer:

```
cat ~/.ssh/id_rsa.pub
```

---

### Post by matt18 on 2019-03-29
"You may use keys that's prefectly normal, but where did you place them?"

I placed the public key on my ssh server(windows 10) by using the import button on the bitvise ssh server key manager. My public key has been added to the server. I can connect to the server from most hosts except my ubuntu host. 

the folder .ssh does not exist on my server since it is windows. However, it does exist on my ubuntu client:) this is where my private key is located, but ubuntu wont read it for some reason. how do i add it to the autherized list then?

will the ssh-add command do this?

I cant use the ssh-copy-id command since the server is windows. the output of the ssh-sopy-id command tells me that:)

I just need to know how to add my private key to ubuntu:)

thanks

---

### Post by matt18 on 2019-03-29
YAY!!!! I FINALLY FIGURED IT OUT!!!

ok, here is how i did it:

on Ubuntu client:

mkdire ~/.ssh
folder already exists
chmod 700 ~/.ssh
ssh-keygen -t rsa /home/matt/.ssh/cloud_server_rsa

this created a public key and private key named cloud server

I then copied the key to my windows machine via thumb drive. Opened up bitvise ssh server. went to accounts, clicked on my username, hit import public key. imported the public key, hit save, restarted ssh service.

Ok, on the ubuntu client, i realized i can do a single sign on with ssh-add /home/matt/.ssh/cloud_server_rsa. This will create a known hosts file in the .ssh folder which tells the kernle that as long as this curent ubuntu session is active, the key is known and active as well. I then go to file manager and type:

sftp://USER@IP:5322

it connects and asks for my passphrase. i type it in and BOOM!!!! im in. 

i restarted the ubuntu machine and tried again. nogo. this is to be expected since ssh-add is for single use only and the known hosts file is cleared after a restart. To fix this, go to startup applications and do the following:

click on add. A new popup window appears. name it what ever and then add the ssh-add <path to rsa private key>. then click save. restart the machine.

Now, it has restarted and i can log into my sftp windows server:) I have restarted 10 times to make sure and it works great. I even made a video of it and i am putting it on youtube to show how to do this.

thank you for your help and input. i learned alot about how to do this:)

---

