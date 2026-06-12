---
title: "FTP Support on ubuntu"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by MikeyUbun2 on 2008-12-30
I am wondering if i can view the ftp contents of my website in a folder so i can easily transfer files in ubuntu.
i could do this in windows by creating a new network place with the url of the ftp site.
i havent been able to find this feature in linux though.
if anyone knows of anything i can do it would be a BIG help :-P

---

### Post by ollesbrorsa on 2008-12-30
Nautilus to the rescue (default file manager)! Just do **File -> Connect to server...**. Enter the info for the site you want to connect to and be sure to check the **Add bookmark** check box.

Br, 
ollesbrorsa

---

### Post by RealG187 on 2008-12-30
[http://ubuntuforums.org/showthread.php?t=1011474](http://ubuntuforums.org/showthread.php?t=1011474)

I am having a problem with that...

---

### Post by ubuntu27 on 2008-12-30
[K Desktop Environment]("http://www.kde.org/")'s [Konqueror ]("http://www.konqueror.org/") has the feature to use FTP as if it were your local directories. You can just browse with folders and transfers files with Copy and Paste.

---

### Post by billgoldberg on 2008-12-30
If you don't want to use nautilus, you can use a ftp client.

I use gftp.

---

### Post by MrWES on 2008-12-30
hrmm..I never knew I could ftp from Nautilus. A nice, quick feature.

Thanks,
Bill

---

### Post by billgoldberg on 2008-12-30
> **MrWES said:**
> hrmm..I never knew I could ftp from Nautilus. A nice, quick feature.

Thanks,
Bill

Nautilus is great for ssh as well.

---

### Post by MrWES on 2008-12-30
Uh huh, I was already using Nautilus for that; but I didn't realize I could use it to connect to a public and/or private FTP site. Kind of silly, cuz I've seen the FTP in the drop-down menu...hehe..

And with tabbing in 8.10 it's very useful for drop 'n drag.

Bill

---

### Post by RealG187 on 2008-12-30
Nautilus in 8.10 can fo tabbing? I want to stay at 8.04, can I just update Nautilus?

---

### Post by oldos2er on 2008-12-30
> **MikeyUbun2 said:**
> I am wondering if i can view the ftp contents of my website in a folder so i can easily transfer files in ubuntu.
i could do this in windows by creating a new network place with the url of the ftp site.
i havent been able to find this feature in linux though.
if anyone knows of anything i can do it would be a BIG help :-P

 Places, Connect to Server....

---

### Post by MikeyUbun2 on 2008-12-31
Wow it is really that easy! i was looking through administration and everythig! thanks for your help!

---

### Post by RealG187 on 2008-12-31
I cannot connect to my FTP (See attachment)

---

### Post by r4v4g3 on 2009-01-01
Thanks for all the great info!

---

### Post by oldos2er on 2009-01-01
> **RealG187 said:**
> I cannot connect to my FTP (See attachment)

 Looks like a badly formed URI. Try "ftp.operation420.net"

---

### Post by RealG187 on 2009-01-01
> **oldos2er said:**
> Looks like a badly formed URI. Try "ftp.operation420.net"
You mean without "ftp://" or the username? Cuz if I don't give a username all that comes up is a file that says you cannot be anon. (you can try and see).

That URL works fine in Windows and Firefox in Linux (but I cannot upload)

I have made a test account you may use in helping me:

Username: "test@operation420.net"
Password:"test"

---

### Post by ollesbrorsa on 2009-01-02
Why don't you try a username without a "@" in it? That should do it.

Br,
ollesbrorsa

---

### Post by albinootje on 2009-01-02
> **RealG187 said:**
> Nautilus in 8.10 can fo tabbing? I want to stay at 8.04, can I just update Nautilus?

Probably not, but perhaps the backports repositories have the new nautilus with tabs.

---

### Post by RealG187 on 2009-01-02
> **ollesbrorsa said:**
> Why don't you try a username without a "@" in it? That should do it.

Br,
ollesbrorsa

You need the @, that's the way Yahoo! set it up

---

### Post by RealG187 on 2009-01-02
> **albinootje said:**
> Probably not, but perhaps the backports repositories have the new nautilus with tabs.

Well I I [installed 8.10](http://ubuntuforums.org/showthread.php?p=6480892#post6480892), although sooner than I planned, but 8.10 solved [a problem with my new Laptop](http://ubuntuforums.org/showthread.php?t=1025831)...

---

### Post by Tobis84 on 2009-01-05
Hi
I have somewhat the same problem. When I try to connect to an ftp-server I get "Can't display [email]server@myftp.com[/email] - invalid answer"

How's that?

---

### Post by Tavius on 2009-01-06
> **oldos2er said:**
> Places, Connect to Server....
I have tried this and got an error... I know it is the right address and username, because I have used in windows. I am trying to get this computer to convert fully to ubuntu, but kind of frustrating. 

The message says:

Cannot display location "ftp://johvius@ftp.hosting.ws/" Connection reset by peer

---

### Post by oldos2er on 2009-01-06
> **RealG187 said:**
> You mean without "ftp://" or the username? Cuz if I don't give a username all that comes up is a file that says you cannot be anon. (you can try and see).

That URL works fine in Windows and Firefox in Linux (but I cannot upload)

I have made a test account you may use in helping me:

Username: "test@operation420.net"
Password:"test"

 Sorry for the late reply--I didn't see this post until just now.

 Use the menus Places, Connect to Server, and under the 'Service type' drop-down menu, choose 'FTP with Login,' then plugin the whole URL. Let me know of this works, or not.

---

### Post by RealG187 on 2009-01-06
It doesn't work.

I can only access FTP in firefox, and that's sad

---

### Post by jerome1232 on 2009-01-07
All that seems to happen to me is the password test isn't being taken for that test account. even using ftp from the command line test, test get's rejected.

```
ftp -n ftp.operation420.net
Connected to premium2.ftp.geo.yahoo.akadns.net.
220-Welcome to the Yahoo! Web Hosting FTP server.
220-Need help? Get all details at:
220-http://help.yahoo.com/help/us/webhosting/gftp/
220-
220-No anonymous logins accepted.
220 Yahoo!
ftp> user
(username) test
331-Enter your Yahoo! member password
331 
Password: 
530-Your FTP session could not be opened.
530-If you continue to have problems, please visit:
530-http://help.yahoo.com/help/us/webhosting/gftp/
530 
Login failed.

```

I get the same thing from nautilus comes back asking me to re-enter the password like authentication failed.

---

### Post by oldos2er on 2009-01-07
I logged in successfully using good ol' command line ftp (see below), but can't seem to get Nautilus to work.

ann@ann-desktop:~$ ftp ftp.operation420.net
Connected to premium2.ftp.geo.yahoo.akadns.net.
220-Welcome to the Yahoo! Web Hosting FTP server.
220-Need help? Get all details at:
220-http://help.yahoo.com/help/us/webhosting/gftp/
220-
220-No anonymous logins accepted.
220 Yahoo!
Name (ftp.operation420.net:ann): [email]test@operation420.net[/email]
331-Enter your Yahoo! member password
331 
Password:
230 
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful.
150  Opening ASCII mode data connection for  .
total 16
-rw-rw-r--   1 6339712  1000002      5504 Dec 14 16:48 hotdogstand.theme
226  Transfer complete.
ftp> bye
221-You have transferred 0 bytes in 0 files
221-Total traffic for this session was 488 bytes in 0 transfers.
221-Thank you for using the FTP service on ftp.us.geocities.com.
221 Goodbye.

---

### Post by jerome1232 on 2009-01-07
Your right oldos2er, I just wasn't including the @operation420.net in the user name :).

I'm guessing maybe nautilus needs the folder that your supposed to be connecting to maybe.  This is the error I get with nautilus.

```
Sorry, could not display all the contents of "/ on ftp.operation420.net": The file is not a directory
```

---

### Post by RealG187 on 2009-01-08
Ya, I get the file is not a directory message too.

My master admin account works though... (it doesn't have an @ sign in it) maybe Nautilus doesn't like the @ sign, it even changes it to "%40" when I type it in...

EDIT: oh and sometimes it does the thing where it acts like I typed in the wrong password, even though I didn't...

---

### Post by Dumbestcrayon on 2009-01-08
```
sudo apt-get install filezilla
```

I love that one.

---

