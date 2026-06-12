---
title: "Creating my first FTP server.."
date: 2010-03-20
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-20
I would like to create a secure FTP server in my ubuntu box,being a begginer i have no idea on creating a FTP server..Step by Step information will be more useful..Thanks in advance..

---

### Post by r-senior on 2010-03-20
This should get you started ...

[https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html]("https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html")

---

### Post by HermanAB on 2010-03-20
It is actually quite trivial to install a FTP server.  Both vsftpd and proftpd work out of the box.  You install the package and it works - end of story.  If you want to know why it works, read the man page.

---

### Post by karthick87 on 2010-03-20
I have installed FTP server(vsftpd),so how to access this FTP server from outside so that my friends can download files from my system..

---

### Post by Iowan on 2010-03-20
You'll need to set up your router to port-forward to your FTP server. Unless your ISP issues you a static address, you may also need to use a service like [no-ip.com/]("http://www.no-ip.com/") or [dyndns.com/]("http://www.dyndns.com/").

---

### Post by asmoore82 on 2010-03-20
> **getyourkarthick said:**
> I have installed FTP server(vsftpd),so how to access this FTP server from outside so that my friends can download files from my system..

[COLOR="Purple"][SIZE="5"]![/SIZE][/COLOR]If you want **secure** FTP, no standalone FTP server is necessary.[COLOR="Purple"][SIZE="5"]![/SIZE][/COLOR]

Just install the "openssh-server" package and you're done(except for router/firewall config).
SSH will give everyone, with a local user account, SFTP access to the entire filesystem-
with the same permissions their account would normally have.

For example, they can SFTP up and down with their home folder;
System folders like /usr, /bin would be download only;
/root and some items in /etc would be totally access denied.

In other words, looking back at the OP:
> **getyourkarthick said:**
> I would like to create **[COLOR="Purple"]a secure FTP server[/COLOR]** in my ubuntu box,being a begginer i have no idea on creating **[COLOR="Purple"]a FTP server[/COLOR]**..Step by Step information will be more useful..Thanks in advance..
[emphasis added] ^^[COLOR="Purple"]**these**[/COLOR] are 2 entirely different services

You can also set up SSH to allow only password-free secure authentication with public keys.
Technically this allows your friends' account on a specific computer to gain access,
but if your friends' machine is stolen or compromised, you can simply revoke its key.

---

### Post by karthick87 on 2010-03-23
How to check my FTP connection to ensure that it is working fine?

---

### Post by r-senior on 2010-03-23
$ ftp <hostname>

If you don't get connection refused, it's working. What you do get depends on how you set it up.

---

### Post by karthick87 on 2010-03-24
I get the following error..

```

karthick@Learners-desktop:~$ ftp Learners-desktop
Connected to Learners-desktop.
220 Welcome to FTP service.
Name (Learners-desktop:karthick): karthick
530 Non-anonymous sessions must use encryption.
Login failed.
ftp> 

```

---

### Post by karthick87 on 2010-03-27
Bump for a move..

---

### Post by Gixxy on 2010-03-27
Make your life easy and just install filezilla... runs natively and works like a champ. (also has windows support) I personally like an openSSH server and using SCP. Its so BA, to quickly copy files securely and quickly without having to start an ftp program.

---

### Post by jmr423 on 2010-03-27
So are you connecting to within your internal network or through the internet?  And here is how you setup proftpd. I would recommend using this as you ftp client and uninstalling the other one because i find that it is the easiest to setup. 

Note i would recommend giving your computer a static internal ip and checking if your isp blocks port 21, if thy do it is really easy to configure proftpd to use a different port.

Step 1. go to the command prompt

Step 2. Type in this command, this installs your ftp software.

```
sudo apt-get install proftpd
```Step 3. Type in this command

```
sudo gedit /etc/shells
```and add this to the end of it.

> /bin/false This makes your ftp server more secure. Now save and exit the text editor


Step 4. Create a directory for your ftp so you don't need to worry about someone deleting your system files. type this command into the command prompt.

```
cd /home
sudo mkdir FTP-shared
```Step 5 create a new user that can only access the ftp. type this into the command prompt.
```
sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
sudo passwd userftp
```Step 6. now we need to change the permissions of your ftp folder.

```
cd /home
sudo chmod 777 FTP-shared
```Step 7. --- optional. You may want to edit your proftpd.conf file. to do this i would recommend going to google and reading everything you can. 

This is what i did on a ubuntu server version 9.1 and the ftp access works perfectly

---

### Post by karthick87 on 2010-03-27
Am connecting through internet.

---

### Post by r-senior on 2010-03-27
> **getyourkarthick said:**
> I get the following error..

```

karthick@Learners-desktop:~$ ftp Learners-desktop
Connected to Learners-desktop.
220 Welcome to FTP service.
Name (Learners-desktop:karthick): karthick
530 Non-anonymous sessions must use encryption.
Login failed.
ftp> 

```
Your FTP server is working. As I said, if you don't get "Connection Refused", it's up and running. It's just not allowing you to log in.

It's just the secure connection aspects that you need to sort out now and I shall bow out at this point because I have not done it. See the post by asmoore82 from 6 days ago.

---

