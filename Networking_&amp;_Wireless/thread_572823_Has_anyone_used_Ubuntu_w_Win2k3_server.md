---
title: "Has anyone used Ubuntu w/ Win2k3 server?"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by SonicSteve on 2007-10-10
I think the title mostly says it all but....
I'm a network administrator and the environment that I've been given is entirely Windows server 2003.  
1. Has anyone successfully logged into a Windows 2003 server using a user account that didn't exist locally on the ubuntu machine. For example if I setup a user on the ubuntu box called "user" and that was the only account, I want to login using an account on the server call it "windowsUser". 
2. Any suggestions if this isn't possible? 

I'm not a great fan of Microsoft but that's what I have to work with unless I can prove that Ubuntu Linux can work in the environment. So no pressure but your help is the only chance to further the cause of Linux in my school. I doubt that converting the 5 servers from Win2k3 to Ubuntu server is much of an option.

---

### Post by SonicSteve on 2007-10-11
Giving a bump, hoping to attract a few more eyes.

---

### Post by Boomy on 2007-10-11
Sure it's possible, you are not limited to your ubuntu user names, you can use any username you want when loggin into the 2003 server machines.

---

### Post by tact on 2007-10-11
I am not exactly sure what you are asking....   there are a number of answers that range from
1.  you can browse the w2k3server shares with no particular special setup on the ubuntu box
through....
2.  you can remote desktop into the win2k3 box
to...
3. you can set your box up to authenticate on an AD domain (not sure if that is of issue here) and log onto the domain as any winbox would.

There are so many tutorials in this forum, or via google, that its a job just sorting thru to find what covers your situation exactly.

I have my company issued (was winXP pro) laptop running ubuntu (first 6.10, then 7.04, now 7.10rc).   The corporate LAN/WAN is an AD system.  For my purposes I dont need to do full AD authentication and so hardly any setup needed.

All I did set up was to use CIFS to pass login username/password to the domain controller and automount 3 fileserver shares every time I boot (or connect to the corporate LAN even without a reboot).

Oh...and I run win2k3server in a vmware virtual machine on my laptop, under linux -  just for fun.   ;)

---

### Post by SonicSteve on 2007-10-12
Hey hey!
I like what I hear. I'll clarify my issue when I get into the school. Right now I need to get the family out of bed:)

---

### Post by SonicSteve on 2007-10-16
OK so here is the issue,
We have 2003 server with Active directory. We also have roaming profiles but I doubt that we will get too far with that.
I want to Log into the server, authenticating to a user in the Active Directory. I read on the samba site or somewhere else that this might not work till version 4 of samba comes out. It just wouldn't be practical to setup users on individual Ubuntu systems. I also read that suse or redhat has support for this and they used the existing Samba code. 

So can this be done? Forget about roaming profiles and any of that stuff.

---

### Post by tact on 2007-10-17
what is it on the network that you need to authenticate to the AD for?  

The corporate LAN I use every day is also win2k3 server with AD.   Without ANY special setup to authenticate to the AD I can access all the file server shares, printer shares, etc.  I simply use the same username and password on my ubuntu laptop as I have for the AD.  This just makes it easier when it comes to browsing windows shares.  Other than that no need to authenticate for my purposes.

When you mention it being impractical to set up individual users on ubuntu systems I am still not sure what you are wanting to do.  Are you planning to set up a number of ubuntu machines as public kiosks or something?   Then I see a problem - how to get hundreds of people's username/pwd details on each kiosk machine.

If its just you and your PC accessing the AD then just create yourself a local machine account with the same username/password as you use on the AD, set your network name to the domain name in smb.conf and you are set.  Avoid all the headache of authenticating to the AD

If something else and you must authenticate to the AD (what is that something else?) then there are tutorials for AD authenticating using current samba/kerberos etc....  

Using those tutorials I got my ubuntu laptop as far as getting valid kerberos tickets issued to it by the AD controller and accessing network resources...  but really - for my purposes (access file and print shares) its overkill!   The almost zero setup standard ubuntu install has whats needed.

:)

---

### Post by ~mc~ on 2007-10-17
I am using Ubuntu with Windows Small Business Server 2003 and ISA 2004.

I have an account already setup in Active Directory for Ubuntu machine.

First of all I cannot get access to the internet. I need to configure Ubuntu to work with the ISA 2004 and secondly I need to get Ubuntu to authenticate with SBS 2003 Active Directory as I want to use the Ubuntu machine as a Print Server.

Any assistance with these two problems would be great.

---

### Post by SonicSteve on 2007-10-17
> **tact said:**
> what is it on the network that you need to authenticate to the AD for?  

The corporate LAN I use every day is also win2k3 server with AD.   Without ANY special setup to authenticate to the AD I can access all the file server shares, printer shares, etc.  I simply use the same username and password on my ubuntu laptop as I have for the AD.  This just makes it easier when it comes to browsing windows shares.  Other than that no need to authenticate for my purposes.

When you mention it being impractical to set up individual users on ubuntu systems I am still not sure what you are wanting to do.  Are you planning to set up a number of ubuntu machines as public kiosks or something?   Then I see a problem - how to get hundreds of people's username/pwd details on each kiosk machine.

If its just you and your PC accessing the AD then just create yourself a local machine account with the same username/password as you use on the AD, set your network name to the domain name in smb.conf and you are set.  Avoid all the headache of authenticating to the AD

If something else and you must authenticate to the AD (what is that something else?) then there are tutorials for AD authenticating using current samba/kerberos etc....  

Using those tutorials I got my ubuntu laptop as far as getting valid kerberos tickets issued to it by the AD controller and accessing network resources...  but really - for my purposes (access file and print shares) its overkill!   The almost zero setup standard ubuntu install has whats needed.

:)

My grand vision is to have ubuntu authenticating to the server, for these reasons.
1. Security settings, 
2. So any user can log on to any computer as it is now. Otherwise computer classes and teachers roaming from class to class would be impossible.

Your right that for one system to be stand alone and access the network isn't hard to do but ultimately I would like to see ubuntu as more of school wide option. I'm just setting it up in my lab right now, our other hurdles are proprietary applications that we use to keep track of marking and student information. We'll see.

---

### Post by SonicSteve on 2007-10-17
> **~mc~ said:**
> I am using Ubuntu with Windows Small Business Server 2003 and ISA 2004.

I have an account already setup in Active Directory for Ubuntu machine.

First of all I cannot get access to the internet. I need to configure Ubuntu to work with the ISA 2004 and secondly I need to get Ubuntu to authenticate with SBS 2003 Active Directory as I want to use the Ubuntu machine as a Print Server.

Any assistance with these two problems would be great.

You might try static IP and set all the DNS addresses manually. Also add proxy config to firefox if you have a proxy server. If it works with manual setup you can then try going back to DHCP. This might help you get on the internet but it doesn't even start to help you with AD. We can work together on that one!


**********EDIT**********
I found this article on Linux.com, they used fedora, I wonder if it would work with ubuntu?
[http://www.linux.com/articles/40983](http://www.linux.com/articles/40983)
I'll try it when I get the chance

---

### Post by bdamon on 2007-10-17
I have had AD logins working for some time on a CentOS file server here at work. It is pretty straight forward and has worked well. 

This thread should get you started.


[http://ubuntuforums.org/showthread.php?t=91510&highlight=kerberos]("http://ubuntuforums.org/showthread.php?t=91510&highlight=kerberos")

---

### Post by Turnip311 on 2007-11-09
So from what I understand from searching forums and google, You can not integrate a Ubuntu workstation into W2k3 AD domain with out having a server running Ubuntu doing the authentication for you?

Please some one correct me and point me down the path of enlightment.

I'm new to Ubuntu, but fell inlove with the interface, ease of use, and ease of installation.

Can someone also suggest some documentation on User Security within the Ubuntu file system?

Cheers!

Turnip

---

### Post by SonicSteve on 2007-11-11
> **Turnip311 said:**
> So from what I understand from searching forums and google, [B]You can not integrate a Ubuntu workstation into W2k3 AD domain with out having a server running Ubuntu doing the authentication for you?
[/B]
Please some one correct me and point me down the path of enlightment.

I'm new to Ubuntu, but fell inlove with the interface, ease of use, and ease of installation.

Can someone also suggest some documentation on User Security within the Ubuntu file system?

Cheers!

Turnip

This isn't what I've understood in my reading, you may be right but I don't think so. Now we really need someone to set us straight. From what I've read it seemed that what you really need is simply samba but samba with much tinkering and modding. To this point I haven't had the time to give it a go.

---

### Post by ugm6hr on 2007-11-19
Not 100% certain what you are looking for - but this seems promising:
[https://help.ubuntu.com/community/ActiveDirectoryWinbind-SADMS](https://help.ubuntu.com/community/ActiveDirectoryWinbind-SADMS)

Seems to give a GUI for logon to Active Directory.  Supports Ubuntu, and available as .deb.

I'm afraid I don't really understand it well enough to know any more than that.

---

### Post by metoor30 on 2007-11-19
If you want to use your Ubuntu machine to login to a Windows Active Directory domain with a Windows Active Directory user, follow the link that bdamon posted.  That howto should allow you to login directly to a windows domain just as you would (in terms of authentication) if you were running a windows client.  This is done through Kerberos.  If you want the real definition of Kerberos (non-windows), do a search on Wikipedia.

---

### Post by SonicSteve on 2007-11-20
Thanks to both of you. I hope to give them a try before this week is out. Just to try to clarify again I administer a Windows 2k3 domain at my school. I would like to be able to login and gain access to domain resources which of course means authenticating to the Active Directory.

---

### Post by SonicSteve on 2007-11-23
> **ugm6hr said:**
> Not 100% certain what you are looking for - but this seems promising:
[https://help.ubuntu.com/community/ActiveDirectoryWinbind-SADMS](https://help.ubuntu.com/community/ActiveDirectoryWinbind-SADMS)

Seems to give a GUI for logon to Active Directory.  Supports Ubuntu, and available as .deb.

I'm afraid I don't really understand it well enough to know any more than that.

I gave this a shot, it does seem promising but wow does it need to be simplified!! I couldn't get it work and there is an overabundance of information with this app. Part of the trouble is that few of the fields that need to be configured have the same name as their W2k3 counterparts making it very confusing. I'm going to  give the other way a shot.

---

### Post by jholzman on 2008-01-25
You should be able to use winbind to do this.  We did it with an NT server before we migrated to a LINUX LDAP server.  It is the same thing really your SAMBA group get pulled in from the Windows groups.  I trying to find out how to do the same thing with a Windows AD server.  We would also like to use ACL's.  the ACL worked for a time, then broke and we went back to the Domain groups.

name resolve order = hosts wins bcast
	idmap gid = 10000-30000
	dns proxy = no
	netbios name = FISH
	printing = cups
	ldap passwd sync = Yes
	idmap uid = 10000-30000
	remote announce = zzz.zzz.zzz.zzz /aaa.aaa.aaa.aaa
	local master = no
	workgroup = home
	syslog only = no
	os level = 0
	ldap admin dn = cn=admin,dc=sefsc,dc=noaa,dc=gov
	socket address = yyy.yyy.yyy.yyy
	printcap name = cups
	security = domain
	max log size = 1000
	winbind separator = +
	log level = 3 passdb:5 auth:10 winbind:4
	log file = /var/log/samba/%I.log
	load printers = yes
	ldap user suffix = ou=people
	socket options = TCP_NODELAY
	wins server = xxx.xxx.xxx.xxx
	auth methods = winbind
	username map = /etc/samba/user.map
	map to guest = bad password
	interfaces = eth0
	domain master = no
	idmap backend = "ldap:ldap://xxx.xxx.xxx.xxx"
	encrypt passwords = yes
	winbind trusted domains only = yes
	winbind use default domain = yes
	logon home = 
	passdb backend = "ldapsam:ldap://xxx.xxx.xxx.xxx"
	enable core files = No
	template shell = /bin/bash
	wins support = no
	ldap delete dn = Yes
	ldap group suffix = ou=groups
	ldap machine suffix = ou=machines
	server string = %h Samba Server
	winbind enum users = yes
	password server = xxx.xxx.xxx.xxx
	winbind nested groups = yes
	ldap suffix = dc=xxx,dc=yyy,dc=gov
	default service = NeverBackedUp
	logon path = 
	acl compatibility = auto
	winbind enum groups = yes
	panic action = /usr/share/samba/panic-action %d
	ldap idmap suffix = ou=idmap
	preferred master = no
	bind interfaces only = true
	domain logons = no
	pam password change = no
# ---Ldap
#        idmap backend = ldap:ldap://xxxx.gov
#        passdb backend = ldapsam:ldap://xxxx.gov
# ---network
# ---samba
#        host msdfs = no
#        msdfs root = no
#   syslog =1(err)2(warn)3(notice)4+debug

---

### Post by SonicSteve on 2008-02-11
I found what may be a perfect way around this problem. 

Ubuntu Terminal Server Client. It works perfectly and gives me more access to the resources I need than logging in as a workstation. 
This way I have access to the Active directory listing, full access to the printers, DHCP, Backup jobs, Everything!!

I have Ubuntu now as my main workstation OS and when I need to be the network administrator I simply pick one of the three servers and log into it with the terminal server client. 

I will still work on getting ubuntu to log into Active directory but for now this actually accomplishes more.

---

