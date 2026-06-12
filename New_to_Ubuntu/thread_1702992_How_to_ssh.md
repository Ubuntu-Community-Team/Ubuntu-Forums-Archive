---
title: "How to ssh?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by 007casper on 2011-03-08
I had a major frustration on creating a secure ssh network. I tried many scattered information on the net, and made a spaghetti out of the whole task while trying to figure things out.  Now, I realize that it is super easy.

I used this thread to solve my ssh problem, I thank everyone who has helped me out.  I updated all the information on this original post, so you don't have to go through thread pages.

There are a lot of tutorials out there.   Majority of them great.  Because of all the variety of information, it is also very easy to get lost.  I hope this 'how to guide' will save you time.  Certain areas might seem repetitive, people tend to jump around.  It is best to read it through a few times, and then tackle it.

If you have any suggestions, or questions, please let me know.


[B]
===========================================
BEGINNERS
===========================================[/B]
client refers to your local computer; 
server refers to your remote server.

Ideally, you want to connect to your server on LAN (Local Area Network) first, then reconnect on WAN (Wide Area Network).  

If you have a laptop, or can get access to one.  Take it by the server and hook it up to a local network.

If you connect on lan first, you can troubleshoot much easier, and you wont be locked out.

check if your server router has port 22 forwarded, also make sure your server has port 22 open.  Remove firewall, and ftp for now.  Make sure you have openssh-server, and openssh-client installed.

Having a GUI(graphical user interface) installed on your server is a security issue, nevertheless if you have GUI on the server you can ssh fast. Here it is.

1- forward port 22 on your server to access everything on the server computer from another computer, go to:
2- Places > Connect to Server
3- choose ssh
4- use localhost and leave other fields blank

that&#8217;s it, do this on both the server, and the client. Easy as pie.  You are set

then, on your client you should be able to login to your remote server.
> ssh remoteuser@remotebox




If you are doing it traditionally without GUI ;)
--------------------------
1- again completely remove any ftp software you already have installed, disable firewall, maybe even remove it temporarily
2- make sure to forward port 22 on your router, and your client/server has port 22 open
3- sudo apt-get update

the openssh-client should be installed on your local machine, and openssh-server should be installed on the remote computer.  However, you can install both openssh-client and openssh-server on the server, and the client.

4- sudo apt-get install openssh-server openssh-client
5- ssh localhost or ssh user@server or ssh username@IP address (or hostname)
you will get...> 
The authenticity of host &#8216;localhost (127.0.0.1)&#8217; can&#8217;t be established.
RSA key fingerprint is 98:8a:b8:b2:2e:8a:53:e0:d5:09:27:fb:74:f0:de:d4.
Are you sure you want to continue connecting (yes/no)?

Looks like it&#8217;s working! Naturally our ssh client doesn&#8217;t have the key for the server, since we just installed it. You can type yes to continue or just hit Ctrl-C to stop.

Then, from the client
> ssh user@server
or
> ssh user@serverIP

you should be asked for a password

** optional:
5a- create a new user on your computer (server) and set their home directory & password
5b- connect to the server with SFTP (FileZilla) with the username and password you created and ensure that you have select SFTP option

That's all there is to it.  

If you are stuck, please check TROUBLESHOOT - Beginners down below.  

As stated before, connecting locally without being in a remote location is the best option.  You can connect your client (maybe laptop) to your server on a local network. If you can connect without a problem on lan, then, you may connect to your server from a remote location.  Please, see the SECURITY section to improve your encrypted connection.



**TROUBLESHOOT - Beginners**
----------------
If it doesn't work make sure, you forward port 22 on your router on the remote server/computer/machine is listening (not the client computer).

to see port is open you can check with 
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

or if you have GUI on the server, you can scan your ports, 
applications>Preferences>Networking Tools

if its not in preferences tab check in admin

click the port scanner tab, enter the ip. If port 22 is open it will show up.

or you can type on the terminal
nmap -v -A ip_address or nmap -v -A -PN ip_address

Also, check file /etc/ssh/sshd_config and you should make sure the server is in fact listening on port 22. You should see lines at the top of the file that say this:
Port 22

Then, make sure ssh server started.
> sudo /etc/init.d/ssh start

make sure sshd is running
> ps -aef | grep sshd

once you've confirmed that, also on the server, look in /var/log/auth.log. You should see messages like:
> Feb  3 19:44:55 bender sshd[740]: Server listening on :: port 22.

and you should see any login attempts that have failed.

if it doesnt work then 
> sudo service ssh restart

if you get, permission denied.
> ssh localhost
permission denied
make sure you have right permissions, and make sure firewall is disabled.

you tried everything, and you follow the instructions.  However, it doesnt work.  Most likely something went wrong.  You should start over

on the server and the laptop
> rm ~/.ssh/known_hosts

on the server
> ssh-keygen -R www
apt-get remove --purge openssh-server
reboot the server, then
> 
apt-get install openssh-server
apt-get install openssh-client
sudo apt-get update
/etc/init.d/ssh restart

take it from the top, please follow steps carefully.  It should work without a problem.

[B]===========================================
SECURITY
===========================================[/B]
Avoiding denial-of-service attacks, port scanning and the like. Rather than using the standard port 22, particularly if you are opening a port to the internet, go into

1- /etc/ssh/sshd_config
and change the port to something else other than 22, save the file. Then, restart the service using

2- sudo /etc/init.d/ssh restart

to restart the service listening on your non-standard port. This is great to prevent the script kiddies from smashing you with brute force attacks.

other places that covers port number revision
check [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

[http://techie-buzz.com/foss/change-default-ssh-port-in-linux.html](http://techie-buzz.com/foss/change-default-ssh-port-in-linux.html)
[http://ubuntuforums.org/showthread.php?t=253460](http://ubuntuforums.org/showthread.php?t=253460)
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

to set your port number you may want to
> sudo netstat -tlnp
The above should show you what programs are on what port.

If everything works, enable firewall
> 
sudo ufw allow 80
sudo ufw allow 22

If the SSH server is listening on a port other than port 22 (the default), you can specify that in your connection (with the -p option). For example, if the SSH server is listening on port 11022, connect: 
ssh -C [email]joe.friday@remote.computer.xyz[/email]:11022

    or 

ssh -C remote.computer.xyz -p 11022 -l joe.friday

If you have made a public/private key using ssh-keygen(please, see how to create keys down below intermediate/advanced section), the private key must be stored in /home/user/.ssh. The key should be accessible only to user. Permissions are very important.  If you have encrypted hard drive make sure your keys are set in proper place, please see TROUBLESHOOT - ADVANCED - Encrypted Home Directory section.

sudo chmod 600 /home/user/.ssh/identity

    or 

sudo chmod 600 /home/user/.ssh/id_rsa 

to see the rest of permissions, please go to "TROUBLESHOOT - ADVANCED - Permission denied (publickey)" section.

To login with the key:

ssh -C remote.computer.xyz -p 11022 -l joe.friday



[B]===========================================
CONVENIENCE AND EXTRA MORE SECURITY - INTERMEDIATE / ADVANCED
===========================================[/B]

    Use public and private keys.
    Change the default port 22 to something else.
    Consider using either iptables or a service such as denyhosts or fail2ban.

    Use strong passwords. Here is a great way to make sure your password is strong.
[http://www.passwordmeter.com/](http://www.passwordmeter.com/) 
[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm) 
[https://help.ubuntu.com/community/StrongPasswords](https://help.ubuntu.com/community/StrongPasswords)

Default Config Files and SSH Port
    /etc/ssh/sshd_config - OpenSSH server configuration file.
    /etc/ssh/ssh_config - OpenSSH client configuration file.
    ~/.ssh/ - Users ssh configuration directory.  It is a hidden file in your user directory.
    ~/.ssh/authorized_keys or ~/.ssh/authorized_keys - Lists the public keys (RSA or DSA) that can be used to log into the user&#8217;s account
    /etc/nologin - If this file exists, sshd refuses to let anyone except root log in.
    /etc/hosts.allow and /etc/hosts.deny : Access controls lists that should be enforced by tcp-wrappers are defined here.
    SSH default port : TCP 22

to change and secure your connection, please see this extensive link [http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html](http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)



[B]
Creating a public and private keys.[/B]
----------------

If your SSH server is visible over the Internet, you should use public key authentication instead of passwords if at all possible.

With public key authentication, every computer has a public and a private "key" (a large number with particular mathematical properties). The private key is kept on the computer you log in from, while the public key is stored on the .ssh/authorized_keys file on all the computers you want to log in to.

Public key authentication is a much better solution than passwords for most people. In fact, if you don't mind leaving a private key unprotected on your hard disk, you can even use keys to do secure automatic log-ins - as part of a network backup, for example. Different SSH programs generate public keys in different ways, but they all generate public keys in a similar format: 

1- <ssh-rsa or ssh-dss> <really long string of nonsense> <username>@<host>

It is fairly easy to generate a secure key to allow key-based authentication to the device.  Using key based logins with ssh is generally considered more secure than using plain password logins. Provided you keep the key secure this is more secure than using a UNIX password (PAM).

First, make sure you can use SSH to log in to your remote *NIX computer's user account. Then, proceed and create keys.



[B]
GENERATING RSA KEYS[/B]
----------------
On the client you need to create a ~/.ssh directory in the appropriate users home directory.  If the directory exist, make sure you have the right permissions.  The permissions are really important.

> 
mkdir ~/.ssh
chmod 700 ~/.ssh
cd .ssh
ssh-keygen -t rsa
> 
Generating public/private rsa key pair.
Generating public/private rsa1 key pair.
Enter file in which to save the key (/home/drobbins/.ssh/identity): (hit enter)
Enter passphrase (empty for no passphrase): (enter a passphrase)
Enter same passphrase again: (enter it again)
Your identification has been saved in /home/drobbins/.ssh/identity.
Your public key has been saved in /home/drobbins/.ssh/identity.pub.
The key fingerprint is:
a3:e7:f2:19:a7:eb:fd:f8:19:f1:f1:7b:fe:35:a1:09 drobbins@localbox

a) Please enter a passphrase different from your account password and confirm the same.
b) The public key is written to /home/you/.ssh/id_dsa.pub.
c) The private key is written to /home/you/.ssh/id_dsa.
d) It is important you never-ever give out your private key.


Regarding the encrypted key, you can run the command several ways.
ssh-keygen -t rsa -b 4096 or ssh-keygen -t rsa -b 4096 -f key_name

dont use dsa keys, they are always 1024 bits.

Above commands will generate a two files, one with just the name of the key and no extension, and a key.pub

the -f key_name option specifies the name of the key; if creating key_name creates issues for you, don't use any key_name. If adding 4096 bits creates issues, dont use it either.  Then, simply run
> ssh-keygen -t rsa

.pub == stands for public == placed on the server.

Your public key is now available as .ssh/id_rsa.pub in your home folder.

Congratulations! You now have a set of keys. Please, continue down below.  Now it's time to make your systems allow you to login with them.



Dont just blindly accept the key as good, verify the fingerprint.

sudo ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key.pub

on the server (in this case, localhost). In this example, it&#8217;s not so important, but it&#8217;s good to ask for this from the sysadmin of remote systems you might connect to (or to provide it to your own users). That way, you know the initial connection isn&#8217;t subject to a man-in-the-middle attack.



**CHOOSING A GREAT PASSPHRASE**
----------------
Just like with physical keys, you need to change all your locks if your RSA key is stolen. Otherwise, someone will be able to get access to all your stuff.

If your RSA key has a strong passphrase, it might take your attacker a few hours to guess by brute force. That extra time should be enough to log in to any computers you have an account on, delete your old key from the .ssh/authorized_keys file, and add a new key.

Your SSH key passphrase is only used to protect your private key from someone else. It's never transmitted over the Internet, and the strength of your key has nothing to do with the strength of your passphrase.

You have to choose for yourself whether to use a passphrase with your RSA key. Ultimately, it's a choice between cursing the difficulty every time you have to type it in, or cursing your glibness when someone logs in to all your accounts and changes your password so you can't get in any more.

If you choose to use a passphrase, pick something strong and write it down on a piece of paper that you keep in a safe place. If you choose not to use a password, just press the return key without typing a password - you'll never be asked for one again. 

please, continue to password authentication



**PASSWORD AUTHENTICATION**
----------------
The main problem with public key authentication is that you need a secure way of getting the public key onto a computer before you can log in with it. If you will only ever use an SSH key to log in to your own computer from a few other computers (such as logging in to your PC from your laptop), you should copy your SSH keys over on a memory stick, and disable password authentication altogether. If you would like to log in from other computers from time to time (such as a friend's PC), make sure you have a strong password.



**TRANSFER CLIENT KEY TO HOST**
----------------
Now that you have a key, you must transfer the key_name.pub to the server, to ~/.ssh/authorized_keys. We can easily do this with ssh or ssh-copy-id.
> ssh-copy-id <username>@<host>

By the way, authorized_keys is a file, and not a folder.  Don't create a folder called authorized_keys.  It will be created for you when your run "ssh-keygen -t rsa -b 4096" on the terminal.

ssh-copy-id <username>@<host>
Where <username> and <host> should be replaced by your username and the name of the computer you're transferring your key to.

and transfer key for others. ssh (scp) ~ useful to copy keys for other users.
scp ~/.ssh/id_dsa.pub [email]user@server:.ssh[/email]/authorized_keys
scp ~/.ssh/id_rsa.pub [email]user@server:.ssh[/email]/authorized_keys

To add additional keys to an existing ~/.ssh/authorized_keys, first transfer the key_name.pub to the server as above (remember ssh-copy-id <username>@<host>).

Then add the key to ~/.ssh/authorized_keys

cat id_dsa >> ~/.ssh/authorized_keys
cat id_rsa >> ~/.ssh/authorized_keys

If you created a name for the key.  Follow the instructions below.
Use "ssh-copy-id" to transfer your key directly.
ssh-copy-id -i ~/.ssh/key_name.pub user@server

Specify a (public) key with the "-i" flag.

user = the username you use to log onto the server.

Due to this bug[link]http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=99785[/link], you cannot specify a port other than the standard port 22. You can work around this by issuing the command like this: ssh-copy-id "<username>@<host> -p <port_nr>". If you are using the standard port 22, you can ignore this tip.

You can make sure this worked by doing:

ssh <username>@<host>

You should be prompted for the passphrase for your key: 
Enter passphrase for key '/home/<user>/.ssh/id_rsa':

Enter your passphrase, and provided host is configured to allow key-based logins, you should then be logged in as usual.



**TROUBLESHOOT - ADVANCED - Encrypted Home Directory**
----------------
Encrypted Home Directory
If you have an encrypted home directory, SSH cannot access your authorized_keys file because it is inside your encrypted home directory and won't be available until after you are authenticated. Therefore, SSH will default to password authentication.

To solve this, create a folder outside your home named /etc/ssh/<username> (replace "<username>" with your actual username). This directory should have 755 permissions and be owned by the user. Move the authorized_keys file into it. The authorized_keys file should have 644 premissions and be owned by the user.

sudo mkdir /etc/ssh/<username>
ls -ld /etc/ssh/<username>
sudo chown <username>: /etc/ssh/<username>
sudo chmod 775 /etc/ssh/<username>
ls -ld /etc/ssh/<username>

Then edit your /etc/ssh/sshd_config and add:

AuthorizedKeysFile    /etc/ssh/%u/authorized_keys

Finally, restart ssh with:

sudo service ssh restart

The next time you connect with SSH you should not have to enter your password.

username@host's password:

prompt as usual with password logins, then read on. There are a few things which could prevent this from working as easily as demonstrated above. On default Ubuntu installs however, the above examples should work. If not, then check the following condition, as it is the most frequent cause:

On the host computer, ensure that the /etc/ssh/sshd_config contains the following lines, and that they are uncommented;

PubkeyAuthentication yes
RSAAuthentication yes


If not, add them, or uncomment them, restart OpenSSH, and try logging in again. If you get the passphrase prompt now, then congratulations, you're logging in with a key!



[B]
TROUBLESHOOT - ADVANCED - Permission denied (publickey)[/B]
--------------------------------
If you're sure you've correctly configured sshd_config, copied your ID, and have your private key in the .ssh directory, and still getting this error: 
Permission denied (publickey).

Chances are, your /home/<user> or ~/.ssh/authorized_keys permissions are too open by OpenSSH standards. You can get rid of this problem by issuing the following commands:

chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

after transfer make sure the permissions are right for every file

$HOME drwxr-xr-x
$HOME/.ssh drwx------

and the files contained in $HOME/.ssh :

authorized_keys and id_rsa -rw-------
known_hosts -rw-r--r--
-rw------- 1 root root 1675 Apr 26 12:45 id_rsa
-rw-r--r-- 1 root root 400 Apr 26 12:45 id_rsa.pub



**TROUBLESHOOT - ADVANCED - Debugging and sorting out further problems**
--------------------------------

The permissions of files and folders is crucial to this working. You can get debugging information from both the client and server.

if you think you have set it up correctly , yet still get asked for the password, try starting the server with debugging output to the terminal.

sudo /usr/sbin/sshd -d

To connect and send information to the client terminal

ssh -v ( or -vv) username@host's

or

ssh -v -v -v mystery



[B]===========================================
WHAT ELSE?
===========================================[/B]
No matter how your public key was generated, you can add it to your Ubuntu system by opening the file .ssh/authorized_keys in your favourite text editor and adding the key to the bottom of the file. You can also limit the SSH features that the key can use, such as disallowing port-forwarding or only allowing a specific command to be run. This is done by adding "options" before the SSH key, on the same line in the authorized_keys file. For example, if you maintain a CVS repository, you could add a line like this:

command="/usr/bin/cvs server",no-agent-forwarding,no-port-forwarding,no-X11-forwarding,no-user-rc ssh-dss <string of nonsense>...

When the user with the specified key logged in, the server would automatically run /usr/bin/cvs server, ignoring any requests from the client to run another command such as a shell. For more information, see the sshd man page. /755



[B]
===========================================
Known_hosts
===========================================[/B]
The server identifies itself with a ssh key pair as well. The server identification is added your account on the client under "~/.ssh/known_hosts" (you will be asked if you wish to add the server identification to known_hosts the first time you connect to a server).

If you later receive an error message, take care to figure out why. The most common reason for this is that the server keys were changed. Your server administrator should notify you if this is the case.

The most concerning reason for this error message, however, is that someone may be trying to spoof your ssh server. This is sometimes called a "man in the middle" attack.

See the security section above for an example of an error message.



[B]===========================================
Running commands on the server with ssh
===========================================[/B]
You can use ssh to run a command on the server.
ssh user@server "sudo service apache2 start"



I didn't write all these instructions.  I wanted to package all the sources into a convenient place.  At the bottom of the page, you will see credits/resources/links where the information was taken.

[B]===========================================
CREDITS
===========================================[/B]
David Planella; bodhi.zazen; yeats; Dorsenstein; djyoung4; c_cinq; WinterMadness; lkraemer
resources:
[http://bodhizazen.net/Tutorials/SSH_overview](http://bodhizazen.net/Tutorials/SSH_overview)
[http://www.ibm.com/developerworks/linux/library/l-keyc/index.html](http://www.ibm.com/developerworks/linux/library/l-keyc/index.html)
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[http://www.howtogeek.com/howto/ubuntu/setup-openssh-server-on-ubuntu-linux](http://www.howtogeek.com/howto/ubuntu/setup-openssh-server-on-ubuntu-linux)
[http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)
[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)
[http://ubuntuguide.org/wiki/Ubuntu:Natty#SSH](http://ubuntuguide.org/wiki/Ubuntu:Natty#SSH)
[http://www.passwordmeter.com/](http://www.passwordmeter.com/)
[http://www.cyberciti.biz/faq/ssh-password-less-login-with-dsa-publickey-authentication/](http://www.cyberciti.biz/faq/ssh-password-less-login-with-dsa-publickey-authentication/)
[http://openssh.com/](http://openssh.com/)
[https://help.ubuntu.com/community/SSH/OpenSSH/Advanced?action=show&redirect=AdvancedOpenSSH](https://help.ubuntu.com/community/SSH/OpenSSH/Advanced?action=show&redirect=AdvancedOpenSSH)







OLD POSTS
--------------------------------------------------------------------------
update 06-14-2011
> 
ssh localhost


works like a charm on lan, I havent tried wan yet.  

Having issues with keys.  It doesnt prompt me for a passphrase.  It still asks for a password.

--------------------------------------------------------------------------
update 06-10-2011
> 
ssh localhost
permission denied

still cant ssh between server and the local computer.  Please, advise.  Thank you.

------------------------------------------------------------------------------------


ORIGINAL POST
------------------------------------------------------------------------------------

port 22: Connection refused - tried several things.  I cant seemed to make it work.

Once all the questions are answered, I am going to edit this original post here, so everyone can use it as a guide.

While back I followed a post regarding how to ssh without knowing what I was doing at all. I couldnt make it work, and I cant find that post for the life of me.

So, I hit the manual, searched.  I tackled it one more time.  I decided to go for it from stratch, while keeping the old files in the /etc/ssh, and in .ssh folder from my previous attempt. 

I followed this link
[https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html)

ssh-copy-id username@remotehost

moe@hmm:/etc/ssh$ ssh-copy-id moe@178.249.152.2
ssh: connect to host 178.249.152.2 port 22: Connection refused

I am having a hard time establishing ssh. I do have a static IP.  I opened up the port on router.  I tried iptables.
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

cant seemed to allow port 22 connection.  By the way, I would prefer to use a different port number than 22.

> 
moe@hmm:~$ ssh -vvv [www.domain.com](www.domain.com)
OpenSSH_5.3p1 Debian-3ubuntu5, OpenSSL 0.9.8k 25 Jan 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to [www.domain.com](www.domain.com) [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
debug1: Connecting to [www.domain.com](www.domain.com) [192.168.1.5] port 22.
debug1: connect to address 192.168.1.5 port 22: Connection refused
ssh: connect to host [www.domain.com](www.domain.com) port 22: Connection refused

please advise thank you.

---

### Post by yeats on 2011-03-08
Hi,

You might be overthinking this a bit, IMHO...  For ssh to work, you need openssh-client installed on the client (it's installed by default on Ubuntu) and openssh-server installed on the server.  Then from the client do:

```
ssh username@IP address (or hostname)
```

you would then enter your password (for the server's account) to authenticate.

On Ubuntu machines out of the box, I have not had to fuss with firewall settings, though if you have set one up, you will need to make an allowance for it.  I would disable the firewall as a debugging measure to see if that's why port 22 is blocked.

---

### Post by Dorsenstein on 2011-03-08
Use [this link]("http://portforward.com/") to help you forward ports. It has general instructions as well as specific instructions for a large number of routers.

Second, try [this link]("http://canyouseeme.org/") to check if the port was opened correctly.

You need to have the port forwarded on the machine you want to connect **to**, not the machine you are using. Also, the ssh server may not be started on the machine you are trying to connect to, which can be fixed by typing this command in the terminal of the machine you want to connect to.
```
sudo /etc/init.d/ssh start
```

---

### Post by djyoung4 on 2011-03-08
are you trying to ssh into a website or a remote box.

---

### Post by c_cinq on 2011-03-08
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)
great tool. it verifies that the port is open.

---

### Post by 007casper on 2011-03-08
I might be overthinking this.  Years ago I was able to ssh to local computers at home without knowing how I did.  Then, recently I needed to set up a remote box. I just cant seem to make ssh work. As I stated before, I tried while back by following a post on the forum.  It didnt work, and I figure I will try it again some other time. I cant find that post.  So, I tried to understand what I am doing, and tackle this once for all.

client= local computer
server= remote server

@djyoung4
yes, trying to connect to a remote box

I tried to have the port forwarded on the server. Then tried 'ssh localhost' on the server. It just gave me 'port 22: Connection refused'

on the remote box (server) I have both openssh-client, and openssh-server installed.
on the local computer again I have both openssh-client, and openssh-server installed.

so client is the local computer, and server is the remote box.  Is that right?  If thats the case, then I can delete openssh-client on the server, and openssh-server on the local computer. Please, confirm.

I know remote box doesnt have 'port 22' open, I tried suggested commands anyhow.

on the local computer I tried to connect to the server
ssh username@IP address (or hostname)
> 
luke@lotus:~$ ssh moe@178.249.137.52
ssh: connect to host 178.249.137.52 port 22: Connection timed out
luke@lotus:~$ ssh [email]moe@www.domain.com[/email]
ssh: connect to host [www.domain.com](www.domain.com) port 22: Network is unreachable

> 
then went to [http://canyouseeme.org/](http://canyouseeme.org/)
on the local computer tried port 22
Error: I could not see your service on 78.95.238.566 on port (22)
Reason: Connection timed out

however, this local computer is able to connect to other shell accounts I have on other servers.  So, I am assuming I dont need to have port 22 open on my local computer.

> Also, the ssh server may not be started on the machine you are trying to connect to, which can be fixed by typing this command in the terminal of the machine you want to connect to.
I did do a complete shutdown on the server, and reboot it.  Maybe I ought to sudo /etc/init.d/ssh start

the post that I followed last time had instructions to use a different port number other than 22.  I cant even find it through google.  I used a port number range that was suggested.  When I do netstat -l, or netstat -pant on the server, I see that port that I set up last time is available on the server in LISTEN state.  Since I dont remember the passphrase, and cant tell the difference between keys that created, I am a bit at a loss. I am trying to figure out what I am doing wrong, and make this work.

thank you for all your help

---

### Post by WinterMadness on 2011-03-08
try port scanning the server to make sure the ssh service is running.

you can use networking tools that comes with gnome or nmap.

To me, it just seems like the server isnt running on the remote machine.

You dont really have to do anything on the client side other than have the ability to use ssh, which you do.

EDIT: I just saw you say you know that port 22 on the server isnt open.

Make sure you configure your firewall correctly on both your router and your OS. Port forward it, open the port on the OS or disable the firewall temporarily.

---

### Post by yeats on 2011-03-08
Two more suggestions:

1) on the server, open the file /etc/ssh/sshd_config and ensure that the server is in fact listening on port 22.  You should see lines at the top of the file that say this:

```
# What ports, IPs and protocols we listen for
Port 22

```

2) once you've confirmed that, also on the server, look in /var/log/auth.log.  You should see messages like:

```
Feb  3 19:44:55 bender sshd[740]: Server listening on :: port 22.
```

and you should see any login attempts that have failed (though it sounds like you haven't gotten that far.

Also, if you can have client and server on the same LAN, do that too for troubleshooting purposes.  Add things like port forwarding after you've confirmed the basics work.

> If thats the case, then I can delete openssh-client on the server, and openssh-server on the local computer. Please, confirm.

I wouldn't remove anything.  You might need to ssh into the client sometime, and it's expected that openssh-client is install on any linux machine.

---

### Post by 007casper on 2011-03-08
how do you scan ports?

when I did netstat -l it does list the port number that I set before for ssh as in LISTEN state.
Last night, I did set port number 22 on sshd_config... then, set the router port range forwarding

application	start	end	tcp udp		IP address
ssh		22	22	both		192.168.1.5

didnt have any luck....

I will take a laptop with me and will try to connect in LAN first through the laptop.

I am going to edit sshd_config file to port 22

then I am going to restart ssh
sudo /etc/init.d/ssh restart

do I have to create ssh keys again? Please, confirm.

If I do need to create ssh keys again.  I will do these as follow...

ssh-keygen -t dsa

ssh-copy-id username@remotehost
if it doesnt work, it will give me an error that it cant connect to port 22 again.

thank you so much for all your help

---

### Post by WinterMadness on 2011-03-08
if youre using gnome, just goto applications>Preferences>Networking Tools

if its not in pref. its in admin

click the port scanner tab

enter the ip. it will tell you ever port open. if 22 isnt there, 22 isnt an open port, and that would be your problem.

You need to make sure the remote computer has the ssh server listening, that the remote machine(not the local machine) is correctly port forwarded and that the firewall is setup properly.

---

### Post by yeats on 2011-03-08
> **007casper said:**
> 
do I have to create ssh keys again? Please, confirm.

No - you do not need to create new keys

> 
ssh-copy-id username@remotehost
if it doesnt work, it will give me an error that it cant connect to port 22 again.

Just try 'ssh username@remotehost' to begin with.  Once you know you can ssh in, then copy your id over for password-less access.

---

### Post by 007casper on 2011-05-27
I tried again.  It gave me 'permission denied' even though I put the proper permissions.

---

### Post by 007casper on 2011-05-30
I checked out this link
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

I still get permission denied.  I even tried
> 
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

I have a better understanding of it now.  I did bring the firewall down, was able to get port 22 open on the router.  Regenerated keys etc.  I just dont understand why it thinks I dont have the permission.

---

### Post by lkraemer on 2011-06-01
I'd suggest doing one of two things.  If your server has a setup feature for
"Enable keyboard-interactive authentication", you can ENABLE this feature long
enough to get it all working. Then, DISABLE it to test your login with DSA Keys.

Also, if you have your Router Ports "OPEN" during this setup, you should really
"CLOSE" all your Router Ports, then connect locally to your LAN and do the 
setup testing so you are the ONLY one setting up your Server.  After it's functional
with your setup and testing complete, then ENABLE just the Ports you need on the
Router.  And keep an eye on the Server's logs to know who is attempting to login
and get access, xfer, and other activity.

Another thing I see that is a problem with your SERVER key authentication is the
permissions for:
> 
chmod 700 ~/.ssh

which should be changed to:
```

chmod 711 ~/.ssh

```
Also, your USER:GROUP of SERVER ~/.ssh may not be set properly in your Server, and you will need to read up
on what it needs to be set for as per your Server Documentation.  Then if your DSA Keys are placed properly,
and you DISABLE "Enable keyboard-interactive authentication", you should be able to login with your DSA Keys
normally via ssh.

Also, you can use :
```

ssh -v loginusername@serverIPaddress
OR
ssh -v loginusername@Hostname.Domain

```
to get more information.

If you are using FreeNAS or Superb Mini Server, their forums can offer good support, with Guides,
Tutorials, and HOWTO:........

LK

---

### Post by 007casper on 2011-06-05
I will try 711.

is the link not up to date
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by lkraemer on 2011-06-07
You can try 711, and if that works, then try 700.  On Debian Laptop with
FreeNAS I must use 711.

lk

---

### Post by 007casper on 2011-06-10
I did chmod 711 ~/.ssh

open up the router on port 22
> 
application   start   end  tcp/udp   ip address
ssh           22      22     both    192.168.1.8

then enable the firewall
> 
ufw incoming deny & outgoing deny
allow 80 tcp
allow 22 tcp

tried 
> 
ssh localhost
permission denied

checked 
/etc/ssh/sshd_config
port 22 is good

scan port 22 through network tools.  It is good.

checked /var/log/auth.log
it is good.  It is listening.

tried
> 
ssh <name>@<serverip>
permission denied

> 
ssh -v <name>@<serverip>
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 208.90.153.1 [208.90.153.1] port 22.
debug1: connect to address 208.90.153.1 port 22: Connection timed out


while back as I stated before I tried to connect through ssh by creating keys without any luck.  I just followed the steps that I found online without understanding it fully.  I am wondering if the old settings are causing issues.

Also, my hard drive on the server is encrypted.

Wanted to give it a try one more time.

I completely removed ftp this time from synaptic(I have gui on the server, I know it is a security issue, and will remove it when I get the complete picture); 

I deleted the old keys from the .ssh/authorized_keys file.  Then, checked /etc/ssh... I had the following files
moduli
sshd_config
ssh_host_dsa_key
ssh_host_rsa_key
ssh_config
sshd_config.default
ssh_host_dsa_key.pub
ssh_host_rsa_key.pub

completely removed openssh-server; openssh-client through synaptic.  The files in /etc/ssh showed only sshd_config.default.  

I installed openssh-server;openssh-client.  The same old files in /etc/ssh showed up that I listed above.

should I just delete the files in /etc/ssh? And then, insert the moduli, and ssh_config files from my local computer to the server.

In any case, just like before checked 
/etc/ssh/sshd_config
port 22 is good

scan port 22 through network tools.  It is good.

checked /var/log/auth.log
it is good.  It is listening.

disable the firewall all the way
> 
ssh localhost

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f2:92:1d:da:81:2a:d7:16:0a:48:f0:43:20:1c:f4:b5.
Please contact your system administrator.
Add correct host key in /home/hiya/.ssh/known_hosts to get rid of this message.
Offending key in /home/hiya/.ssh/known_hosts:2
RSA host key for localhost has changed and you have request strict checking.
Host key verification failed.

:(

enable the firewall back to 
incoming deny & outgoing deny
allow 80

closed port 22 on the router

havent done "rm ~/.ssh/known_hosts" or "ssh-keygen -R hostname" yet

how can I wipe the old settings?  How come old /etc/ssh files shows up after complete removal and install of openssh-server and client.  Why do I get permission issue?  Is it because of encrypted hard drive, so I assume home directory encrypted.  How can I test ssh without bringing ufw down?

thank you so much for all your help.

---

### Post by 007casper on 2011-06-10
bump

---

### Post by 007casper on 2011-06-10
My local computer has only two files ssh_config and moduli.  The server has all these other files from my previous attempts
> 
sshd_config, ssh_host_dsa_key, ssh_host_rsa_key, sshd_config.default
ssh_host_dsa_key.pub, ssh_host_rsa_key.pub


should I delete the files that is listed above from /etc/ssh?

and only leave 
ssh_config, and moduli


I just don't want to ruin the system more than it is.

Please, advise.  Thank you.

---

### Post by 007casper on 2011-06-10
bummer... no response.  I really need to sort this out.  If anyone can help out, that will be great.

Thank you.

---

### Post by lkraemer on 2011-06-11
I'd suggest the following:
1.  CLOSE ANY OPEN Router ports for your testing.
2.  Connect to your Server over your LAN ONLY......NOT WAN
3.  Enable one thing at a time on your Server, and test it's operation.
4.  When you understand how that Service works, move to the next.

With your Router ports CLOSED, you can still access your Server from the
LAN with your Client.  ie.. ssh loginbozo@192.168.1.250

I would suggest starting with SSH, then FTP, then NFS, then CIFS/SMB, then
on to what ever you need/desire.

For your testing start with Password Authentication, with your Server set
to a STATIC IP Address on your LAN.  Once that works, add Key Authentication.
Then add one Service or Function at a time, to build what you need in your Server.

I'd think that if you removed the key files on both the Server and Client, along with the
known_hosts, and authorized_keys files, assuming Version 2 keys, you should be good to
start over.  ie...
authorized_keys
authorized_keys2
known_hosts
id_dsa
id_dsa.pub
id_rsa
id_rsa.pub

Once you can ssh into your Server with Key Authentication, then you can Open your Router's
Port 22 ONLY and test ssh, keeping an eye on your Log files.  Then, if you aren't getting
probed/attacked/accessed you can try Opening Port 21 for FTP transfers with sftp via Filezilla.
Not regular ftp transfers because your login & password are transmitted in the clear.

Here is some good information for FreeNAS, but won't apply to your Server.
Although the method will apply.  It's going to take some time, and you will learn
a lot.  Just go slow and understand what you did in the process.

[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=48&t=11275](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=48&t=11275)

lk

---

### Post by 007casper on 2011-06-14
it seems as I am moving on the right direction.  I closed the ports, and I was able to create ssh on lan.

It is suggested that I create the keys on the linux client and then transfer the .pub key...
ssh-keygen -t rsa -b 4096 -f key_name

why do I need to create the keys on a Linux client?  Can I create the keys directly on the server since I have physical access to it?

Thank you.

---

### Post by 007casper on 2011-07-02
I thank everyone that has helped me out on this ssh task.  I revised the original post and updated the tutorial.  If you have any questions, or suggestions, let me know.

---

