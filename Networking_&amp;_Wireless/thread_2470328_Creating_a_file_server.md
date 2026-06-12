---
title: "Creating a file server"
date: 2021-12-26
forum: Networking &amp; Wireless
---

### Post by deads2 on 2021-12-26
Hi all. Hope you're all having a great Christmas break. 

I've just recently set up a Poweredge R620 server. I'm looking to run a file server. Wondering if its possible to do on Ubuntu and if so, is there anyone here who could walk me through the process of setting it up? Not a whole lot of info on configuring a file server from start to finish online that I can find (surprisingly). Though, there is a bunch of info on setting up a NAS with the specific associated hardware/firmware that comes along with it, but nothing on non-specific file servers.

Help would be appreciated haha.

---

### Post by rsteinmetz70112 on 2021-12-26
What are your goals?
File serving to Linux or Windows clients?

---

### Post by deads2 on 2021-12-26
Goal is to learn how to set up a file server (among many other things) for my place of employment. File serving to windows clients.

Recently got an IT position at my work. Business is expanding and I’ll soon be managing my own network. I don’t have the experience I should have yet (everything at work is changing so quickly lately). So I need to learn as much as I can as quickly as I can. I do that by getting my hands dirty.

I don’t want to bug anyone from work with questions. I like to be resourceful and find my own answers to problems I have. Normally I do that just fine, but there doesn’t seem to be much in terms of setting up file servers. Asking on a forum is my last resort haha.

---

### Post by QIII on 2021-12-26
One thing you may want to do before you launch too quickly is to ask your employer what operating systems, technology and authentication methods they want to have used.

In this case, your employer is your customer.  You should not be dictating what your customer "wants", but implementing a solution based on what they tell you they want.  This can be a long, involved conversation, but it must be done.  Otherwise you risk forcing your "customer" into your vision of what should be rather than theirs.

---

### Post by deads2 on 2021-12-26
> **QIII said:**
> One thing you may want to do before you launch too quickly is to ask your employer what operating systems, technology and authentication methods they want to have used.

In this case, your employer is your customer.  You should not be dictating what your customer "wants", but implementing a solution based on what they tell you they want.  This can be a long, involved conversation, but it must be done.  Otherwise you risk forcing your "customer" into your vision of what should be rather than theirs.

Aptly put. 

Employer provided me with the poweredge to get some general experience with setting up networks and the usual utilities that a network relies on from home.

A file server was one of a few things he recommended setting up.

---

### Post by QIII on 2021-12-26
Understood.  But is your employer coming from a background that includes Linux, or would "server" in his mind be a Windows Server?

---

### Post by deads2 on 2021-12-27
I sent him a message about this yesterday, but haven't heard back from him.  In the mean time, happy to set up 2 x file servers. One on each OS for experience and practice.

The R20 is set up on VMware's Exsi 6.7 OS.

---

### Post by deads2 on 2021-12-27
Disregard

[https://ubuntu.com/server/docs/samba-file-server](https://ubuntu.com/server/docs/samba-file-server)

Stumbled across this and set it up with success. Have to say that Ubuntu has great educational resources for people like myself looking to set things up.

---

### Post by rsteinmetz70112 on 2021-12-27
Sorry for chiming in here but since you are just starting out I thought you might appreciate a little more information.

The link above sets up an NT style server. That is becoming obsolete and Microsoft is moving to eliminate the option forcing a move to  Active Directory which is far more capable and secure but also much more complex. Depending on the number of users and clients you may want to move to security = domain or Security = ADS.

Samba can run as an ADS server. The Link to the Samba Documentation in your link above is to Samba 3.6 and includes setting up domain control including ADS. The current stable version of Samba is 4.14.11  The version on my Ubuntu 20.04 LTS is  4.11.6. Don't get too hung up on the difference. Ubuntu back ports security patches. I prefer to stay with the packages in the Ubuntu repositories as it makes maintenance much easier.

Also if you are running a server always use the LTS versions the most current one is 20.04 with the next one being 22.04 out in a few months. They are good for 5 years while the regular releases are good for only a very limited time.

Hope that helps and good luck.

---

### Post by deads2 on 2021-12-27
> **rsteinmetz70112 said:**
> Sorry for chiming in here but since you are just starting out I thought you might appreciate a little more information.

The link above sets up an NT style server. That is becoming obsolete and Microsoft is moving to eliminate the option forcing a move to  Active Directory which is far more capable and secure but also much more complex. Depending on the number of users and clients you may want to move to security = domain or Security = ADS.

Samba can run as an ADS server. The Link to the Samba Documentation in your link above is to Samba 3.6 and includes setting up domain control including ADS. The current stable version of Samba is 4.14.11  The version on my Ubuntu 20.04 LTS is  4.11.6. Don't get too hung up on the difference. Ubuntu back ports security patches. I prefer to stay with the packages in the Ubuntu repositories as it makes maintenance much easier.

Also if you are running a server always use the LTS versions the most current one is 20.04 with the next one being 22.04 out in a few months. They are good for 5 years while the regular releases are good for only a very limited time.

Hope that helps and good luck.

Definitely appreciate you chiming in! I was keen to set up a couple of these for practice.

I don’t know what an NT style server is. Didn’t know there was options of setting up ADS vs NT style servers. Info like this is exactly what you discover when you get hands on and make inquiries which is great.

> **rsteinmetz70112 said:**
>  The Link to the Samba Documentation in your link above is to Samba 3.6 and includes setting up domain control including ADS 

> **rsteinmetz70112 said:**
>  The link above sets up an NT style server.

So are you saying that an NT and ADS style server can be set up using the version of Samba that I’ve downloaded?

Where do you find the most recent version of Samba? I thought it would be always in the same location.

---

### Post by rsteinmetz70112 on 2021-12-28
> **deads2 said:**
> Definitely appreciate you chiming in! I was keen to set up a couple of these for practice.

I don&#8217;t know what an NT style server is. Didn&#8217;t know there was options of setting up ADS vs NT style servers. Info like this is exactly what you discover when you get hands on and make inquiries which is great.

ADS is based on different protocols including Kerberos, DNS and LDAP all mixed in with some special Microsoft Sauce. The older NT style which is based on LANMAN, SMB1, WINS and other older protocols. The differences are complicated. The most current Samba Information is in the Samba Wiki [https://wiki.samba.org/index.php/Main_Page](https://wiki.samba.org/index.php/Main_Page). Unfortunately there is a lot of older information on Samba and other Linux topics still out there on the Web, a lot of it still works, a lot of it doesn't, some of it is specific to certain distributions  and releases.

There is a script built into Samba which is supposed to convert the old style to the new style but it requires pre-planning. I don't know how well it works, I've never used to. 

> So are you saying that an NT and ADS style server can be set up using the version of Samba that I&#8217;ve downloaded?

Most probably it can, any reasonably recent version can do both, but I don't know what version you have nor what version of Ubuntu your have installed. Perhaps you could tell us..  

> Where do you find the most recent version of Samba? I thought it would be always in the same location.

The most recent stable version of Samba is 4.15.3. It can be found at [www.samba.org](www.samba.org), but I wouldn't try to use that. I'd use the current package from the Ubuntu repositories for the Ubuntu release you're running as that can be automatically upgraded and all of the dependencies will be updated as well. The packages in the Ubuntu repositories are compiled using the current Ubuntu packages and tested to be sure there are no conflicts. or at lease as few as possible. 

A Linux Distribution is made up of hundreds of packages and thousands of files from a large number of sources, getting all that to work together is not a simple task but the major distributions manage it pretty well. I strongly recommend not installing anything not in the repositories on a production computer unless you know what you're e doing and really really need some specific feature. Of course if you're testing stuff out and don't mind reinstalling frequently have at it.

---

### Post by TheFu on 2021-12-28
> **deads2 said:**
>  
So are you saying that an NT and ADS style server can be set up using the version of Samba that I’ve downloaded?

Where do you find the most recent version of Samba? I thought it would be always in the same location.

Linux is different from Windows.  Don't to out on the internet and download software from random places.  Use the package manager.  There are 50 reasons to do this. When you have more experience, it will be clear why. For now, just knowing that you don't want to use a browser to get software is the short answer.

If you installed software from anywhere else, outside the package manager, including downloading packages manually, you are doing it all wrong and making more work for yourself.

NT domains and AD Domains (active directory) are different from the typical way that Linux authentication is performed, but if you are in a Windows-only situation, then that is probably the easiest answer.

As for file servers, there are many, many, many, different sorts of files to be served.  If it is just for Windows computers on the same subnet, then CIFS is probably fine.  But some companies want to provide file sync setups or media files or content management or project management or customer access portals or to have files available for employees when they are away from the office or .... lots of different options.  Out of all of these options, CIFS/Samba is the least capable, though most used in legacy companies.

Often, people want to setup a print server too.  Printing from Linux has become trivial the last 10 yrs - some printers are discovered and configured without **any** end-user setup needed. The printers on the LAN are already listed in every File-->Print for every program on a Linux desktop.  

Alas, seems your company is still using Windows. Too bad.  With Linux clients, there are many better options for file servers.  We can only do as much as the company is ready to take on.

My little company barely uses CIFS.  We tend to use NFS and Nextcloud for our file management needs.  When remote, we use a full VPN to access Nextcloud or sftp which is integrated inside almost every Linux file manager desktop program.  NFS appears like local storage to each system on the LAN, BTW.  Alas, NFS with Windows as the client is non-trivial to setup.

If your company isn't tied to ESXi, might I recommend that before that happens, you consider switching to KVM +libvirt instead?  KVM is 1000x more flexibile, faster, and doesn't have $4K license cost for almost everything.  Normal F/LOSS backup tools can be used too. Last time I checked, which was about 10 yrs ago, the cheapest backup software for ESXi was $1000 and not very efficient.

There are many people here with lots of VM hypervisor experience.

---

### Post by deads2 on 2021-12-28
> **rsteinmetz70112 said:**
> your link above is to Samba 3.6 I prefer to stay with the packages in the Ubuntu repositories as it makes maintenance much easier.


> **TheFu said:**
> Linux is different from Windows.  Don't to out on the internet and download software from random places.  Use the package manager.  There are 50 reasons to do this. When you have more experience, it will be clear why. For now, just knowing that you don't want to use a browser to get software is the short answer.



I’m confused. I downloaded by ‘sudo apt install samba’. Does that not download the most recent version of anything straight from the repositories? (Which is what I meant by it always being in the same location).

---

### Post by TheFu on 2021-12-28
> **deads2 said:**
> I’m confused. I downloaded by ‘sudo apt install samba’. Does that not download the most recent version of anything straight from the repositories? (Which is what I meant by it always being in the same location).

Different releases will have different versions of samba.  So, 18.04 will be different from 20.04, which will be different from 21.10.  Canonical will patch each of those versions for security, but not for new features post-release.  The goal is for the features to be frozen with the released version and to only fix critical bug or security issues in already released versions. This is part of the stability for Linux systems. It is very different from how MS-Windows works, especially with 3rd party software like Samba.  **New is the enemy of stable.** Always remember that.

Samba isn't from Canonical. It comes from the Samba team and Canonical repackages a specific version for each release.  Almost everything in any release by any distro comes from other teams.  When something is "supported by Canonical", that means that they will look at all bugs, decide which are security or critical and patch those. Sometimes the backporting of a critical security bug is extremely difficult, so doing it for 1000+ packages in any specific release is hard.

Understanding what the repos are and are not is something worth learning.

---

### Post by deads2 on 2021-12-28
Interesting… nothing ever seems simple haha &#128514;

---

### Post by TheFu on 2021-12-29
> **deads2 said:**
> Interesting… nothing ever seems simple haha &#128514;

But there is almost always a very good reason for doing things in the specific ways they are done.  There are lots of smart people out there.

If you want a release that always has the latest and don't need stability, check out Arch Linux.  They have a "rolling release" which means that from day to day, versions of underlying software can change.  Sometimes a library that other programs depend on will be updated, breaking 20 library user projects. If you can live with a few days for those programs to be unavailable, then great.  The teams will get the new library and update their code to work with it.

But if you want stability first, as the most important consideration, then only changing those specific things that would be terrible if left unchanged, is the better answer.

Everyone has different needs. There is likely a Linux distro to fit your needs - or at least one that is close enough that you can live with it. If not, you can create your own. ;)

---

