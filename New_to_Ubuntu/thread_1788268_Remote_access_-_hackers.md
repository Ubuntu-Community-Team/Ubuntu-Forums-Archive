---
title: "Remote access - hackers"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-22
I have a wifi network. If a hacker got on to my lan by guessing my wpa password how could he gain access to my ubuntu machine ? I noticed there is a guest account . Is that secure ?

---

### Post by doas777 on 2011-06-22
by default, your computer is secure, because ubuntu ships with no network services enabled. to use an account (guest or otherwise) you need to log in via a network service.
to check the network services you have running, you can run:

```
sudo netstat -ntlup
```
and look for ports listening on address 0.0.0.0. post back any that come up and we can tell you what they are.

your bigger concern with somone having infiltrated your wifi, is eavsdropping. if they can capture your bank password, then they can login to your bank account. standard secure banking protocols (SSL/HTTPS) should prevent this, but it varies from bank to bank, and some banks mix secure and insecure content on a single page (which makes eavsdropping easy).

---

### Post by sanderd17 on 2011-06-22
In the default configuration, a hacker wouldn't be able to access anything, but maybe he could access devices like a network printer.

If you installed servers (like a web server, file share server ...) that listen on certain ports, than a hacker could access that server and view or edit (depending on what the server allows) certain files.

---

### Post by kalimojo on 2011-06-22
> **doas777 said:**
> by default, your computer is secure, because ubuntu ships with no network services enabled. to use an account (guest or otherwise) you need to log in via a network service.
to check the network services you have running, you can run:

```
sudo netstat -ntlup
```and look for ports listening on address 0.0.0.0. post back any that come up and we can tell you what they are.

your bigger concern with somone having infiltrated your wifi, is eavsdropping. if they can capture your bank password, then they can login to your bank account. standard secure banking protocols (SSL/HTTPS) should prevent this, but it varies from bank to bank, and some banks mix secure and insecure content on a single page (which makes eavsdropping easy).

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1066/mysqld     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1116/cupsd      
tcp6       0      0 :::80                   :::*                    LISTEN      1346/apache2    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1116/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           9688/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1132/avahi-daemon: 
udp        0      0 0.0.0.0:53074           0.0.0.0:*                           1132/avahi-daemon: 
udp        0      0 0.0.0.0:513             0.0.0.0:*                           1080/rwhod      
udp6       0      0 :::5353                 :::*                                1132/avahi-daemon: 
udp6       0      0 :::33033                :::*                                1132/avahi-daemon:
```

---

### Post by Mr.Dee on 2011-06-22
Chances are you are okay, your neighbor is probably not a super advanced hacker.  I've been studying wireless security recently.  You will much safer by picking a solid password.  Go with WPA and a password with more than 12 characters, doesn't have to be something crazy... Example, Try a simple word like "password" and shift your right hand on the keyboard and "password" will become "oasswird" throw in a few $$#!#! and you are good.  Not exactly an answer to your question, but might ease your concerns.

---

### Post by sanderd17 on 2011-06-22
Another great tip to create a password: 
[LIST]
[*]think of a phrase that you like (e.g. a little piece of your favourite song)
[*]take all first letters from the words of that phrase
[*]put some capitals, numbers and other signs in it
[/LIST]

I don't even have wpa security. I trust on the that fact that my only neighbour with a computer is not a super hacker. And I might be fairly sure he's not a super hacker because he had a wireless network without protection for more than one year :D

---

### Post by disabled20191128 on 2011-06-22
If you set up a Mac address filter the hacker won't be able to access your wireless access point even if he guesses the password.

---

### Post by CharlesA on 2011-06-22
> **Dennisgre said:**
> If you set up a Mac address filter the hacker won't be able to access your wireless access point even if he guesses the password.
MAC addresses can easily be spoofed.

@OP: It looks like you are running a LAMP server (MySQL and Apache), is that the case?

---

### Post by doas777 on 2011-06-22
hmmm. you are showing two odd network services.
you have an IPv6 listener for apache2, a webserver. do you have any apps that provide a web interface? if not, uninstalling apache2 is not a bad idea.

second, you have a listener on udp\513 for the "Remote Who" service. this allows someone to remotely determine who is logged into the box and provides a little insight into what they are doing. do you have any idea how this got installed? not normal. 

if you want to be on the safe side, install gufw from the repos, and make it look like this:
[IMG]http://ubuntuguide.net/wp-content/uploads/2010/12/gufw_screenshot2-231x300.png[/IMG]

that will block all unsolicited incoming connections, without interfering with any traffic you request.

Note: gufw is not like windows firewall tools. it is just a configuration interface, so you only run it to set your settings once. you never have to run it again unless you want to edit the ruleset. You do not need to add it to Startup applications.

---

### Post by Dangertux on 2011-06-22
First off , much of what has been said here is true. However, there are a few caveats I would like to add.

Cracking a WPA passphrase HAS to be done by brute force, you can't collect IV's like you can with a standard WEP key to crack it. So what was said about the longer password is important. Keeping that in mind using common dictionary terms even with special characters added in is asking for trouble. Randomize, remember your WPA passphrase is not something you have to be repeatedly entering so make sure it's strong. A randomized 12+ character passphrase will take even a fast brute force method hundreds of thousands of years to crack. 

Secondly MAC address filtering, turning off DHCP , and hiding your SSID. Three things that are always recommended and do absolutely nothing for your security.

To capture data sufficient to crack a WPA passphrase your MAC address does not actually have to be associated with the router, you simply have to deauthorize a client that is associated with the router. Since you have to do that, you already have access to a MAC address the router will authorize with the proper key. As far as DHCP goes, if you can do all this, you can take the 3 seconds it takes to set up a static IP address.  Hiding your ESSID (SSID) does nothing the access point will still broadcast on it's BSSID (MAC Address) , so this does little to nothing for you.

As far as if someone does penetrate your wireless network, the above poster stated they can ciphon out many credentials in this method. There is a good chance that you also are reusing your passwords , which means if they have your passphrase they probably also have your password to something else. 

Long story short, change your WPA passphrase to something strong. THAT is your perimeter security for your wireless network. As far as unused accounts it's always a good idea to disable them, however in this situation if you are using an iptables based firewall (such as UFW) you are probably fine if it is in it's default configuration. 

If you are running a LAMP stack (which someone said that you are). You need to make sure your MySQL server is bound ONLY to localhost if it is running on the same machine as the webserver, and that your apache server is properly hardened. Also you should audit any scripts and web applications you are running on your site to make sure that all user input is properly sanitized.

---

### Post by kalimojo on 2011-06-22
thanks for your replies. Yes I am running a LAMP stack. Not sure how rwhod got installed tbh. I am running virtualbox on the machine.

---

### Post by Mr.Dee on 2011-07-26
+1 on Dangertux's security advice.

---

