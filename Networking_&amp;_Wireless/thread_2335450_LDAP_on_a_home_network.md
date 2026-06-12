---
title: "LDAP on a home network"
date: 2016-08-28
forum: Networking &amp; Wireless
---

### Post by jwbrase on 2016-08-28
I'm looking at setting up an LDAP domain between the Linux machines on my home network for SSO and career development purposes. From what I'm seeing, I'm thinking it may be a bit of overkill for SSO purposes, but it would definitely be nice resume-wise to build up experience with LDAP. I'm currently looking at [this]("https://www.danbishop.org/2015/01/30/ubuntu-14-04-ultimate-server-guide/3/") guide, though I haven't started anything yet and may go with different setup guidelines depending on what recommendations I get here.

My network consists of:

[LIST]
[*]A server/superdesktop which is my main computer, initially setup with Ubuntu 14.04 stock, later moved by addition of repositories to Ubuntu Mate. /home on this machine was cloned from the laptop (see below) when the system was built, though the two home directories have since diverged (with /home on this machine being mostly a superset of that on the laptop). This machine will be the LDAP server. It machine runs daily incremental full-system backups, so I'm willing to risk breaking things getting it set up, as I know I can rewind it to a known-good state.
[*]A pair of old PCs that I use for retrograming and experimentation, which multiboot Linux and several legacy OSs (mostly DOS/Win9x), running Debian on the Linux side (Squeeze and Wheezy, according to what the hardware will tolerate, though the less ancient one could probably be upgraded to Jessie). I'll be wanting to add the Debian installs to my LDAP domain, but not, of course, the legacy OSs.
[*]A 7-year old System76 Pangolin P5 laptop. The root filesystem is a fresh install of Ubuntu Mate 14.04 done a year or two ago. /home goes back to when I bought the machine in 2009, so there may be bits of configuration in dotfiles that reflect a system as old as stock Ubuntu 9.04. Due to the fact that the home directory was cloned to the main desktop, this applies to that system as well.
[*]A Raspberry Pi 2 Model B running Ubuntu Mate.
[*]A Raspberry Pi Model A+ running Raspbian Jessie, operating as a GPS timeserver
[*]An OpenWRT router, providing a NATed subnet with sane DHCP and DNS to the household LAN (the firmware on our ISP's CPE router is so buggy that it is impossible to run any kind of LAN on it. It provides connection from individual computers to the web, but falls over as soon as devices on the LAN start trying to communicate locally).
[*]A few Virtual Machines, including a Win10 install, intermittently running on the main desktop. I may at some point in the future set up a personal e-mail and/or VOIP server, if I do, I anticipate that I would use an always-up VM on this machine to do so.
[/LIST]

Additionally, there are several family devices that I don't plan on connecting to the LDAP domain.

I have a few questions:

1) Is there a simpler solution for home networks for SSO purposes? Given that my goals are not just SSO, I may or may not go for such solutions in lieu of LDAP, but I'd like a good overview of my options

2) The guide that I linked recommends (in earlier sections than the one linked) having NTP and DHCP/DNS on the LDAP server. How necessary is this? My impression is that as long as I have a source for these services that everything on my network is pointed at and that I have complete administrative control of, they don't *have* to be on the same machine. It furthermore seems that moving DHCP/DNS from the router to my main desktop would give the whole network an extra single point of failure for internet connectivity: the network fails if either the router or the desktop goes down, rather than just the router.

3) None of the existing machines or user accounts were set up with LDAP in mind. My primary account on all of them has the same name, and this is the name I would like to use for my LDAP user account, each machine, of course, has its own home directory. How much of a hassle will it be to migrate the existing accounts into a unified LDAP account?

4) The laptop may not always be connected to my home network, and it would be good to have robustness against failure of the LDAP server for all machines. What needs to be done to make sure that I can log in to machines locally if for whatever reason they can't connect to the LDAP server?

5) If I'm using the same home directory across all machines, to what degree can I have different X session defaults on different machines? The laptop and desktop support Compiz, the Pi 2 will run MATE but not Compiz, and the remaining physical machines (that aren't headless and X-less) won't support anything heavier than Xfce (and one of those thrashes swap so badly with X loaded that saying that it supports Xfce is dubious). I'm afraid, for example, that since I'm using MATE as my default session on the newer machines (specifically the desktop, as I anticipate that the network home directory would be my current home directory on that machine), my dotfiles will cause the older machines to also default to MATE (though since I'm using different DMs on different machines I'm not sure of that?), which will not run and is not installed on those machines. I'm also concerned that MATE, when starting up on the Pi 2, will attempt to use Compiz and Emerald, which are desirable on the more heavy-duty machines, but won't run and aren't installed on the Pi. Are these valid concerns with a networked home folder? Can anything be done to mitigate them if they are? Is my network too heterogenous for this to be a good idea?

6) Can I make resources on a machine that's part of an LDAP domain available to machines that are on the same network but not part of the domain? For example, can I share a folder to the entire home network (both domain and non-domain machines), or if one SAMBA or NFS share on a machine is administered by LDAP, do they all have to be administered by LDAP? Given my sparse knowledge of LDAP going in, is this question even sensible?

7) The recommendations I'm seeing say that an LDAP domain should generally have a base DN matching the FQDN of the network the domain is operated on. As of yet, I'm just operating on a home network with no domain name and no real visibility from the outside internet, but, as I mentioned, I may at some point in the future operate a home e-mail or VOIP server, at which point I would need a domain name, but as of yet I don't know what that domain name would be. Also, from what I can see, changing the base DN of an established LDAP seems to be a real pain. Can anybody recommend a future-proof way of choosing a base DN in this situation?

---

### Post by TheFu on 2016-08-29
Please be specific about what you want - even "SSO" is extremely generic and means very different things to different people.

LDAP is just a fast read DB and slow write DB.  We can put anything into it - anything.  Historically, it has been used as a replacement to NIS - which is userids/passwords, groups, hosts, and perhaps, DNS. NIS has huge security issues, which make it unsuitable in the world today.  NIS+ is a more secure alternative, but Sun Microsystems never released the NIS+ server code, only the client-side code.  Got a Solaris box?

SSO for Unix logins/authentication using LDAP isn't that hard. Just setup the POSIX extensions to the LDAP schema and set the PAM settings on each client to use them.  1st system will take a few hrs, but after that, it is 5 minutes.  Credentials are cached, so laptops will work off network.  I don't know anything about making Windows work with this stuff. Plus "home" versions don't include LDAP support, so that will be a challenge to SSO on Windows.  Plus Windows doesn't use userids like Unix does. You can have multiple userids with the same name, but they won't have the UUID for network authentications.  For those, you'll need to figure out how to make them match (outside my skills).

If you are running any other services - web, email, imap, DMS, CRM, etc ... and want SSO to those, then each will need to point to the LDAP DB and meet whatever standards are required. Most of these will use the POSIX extensions too. Once found that my 45 character passwords were too long to work with Alfresco (a DMS tool) and had to change the max length to 31 characters because some Java programmer specified the limit inside is web-GUI code even though I was using LDAP for authentication. Expect an issue or two like that.  The 15 other web-services that authenticated with LDAP worked fine.  The nice thing was passwords only needed to be changed in 1 place and all other logins got the change immediately. You'll want to choose 1 system to always change the password through, not all of them. For security reasons, most systems will only have read-only access to the authentication DB, not read-write.

Using NFS for single HOME directories has been done since before Linux existed.  There are complexities due to different hardware having different capabilities. Plus the 32-bit and 64-bit differences will probably matter at some point.  I would hope that Linux has a way to support different config directories (~/.config/ ) by different hostnames - I haven't seen this, but that doesn't mean it doesn't exist.  Only ponder this on systems that don't leave the subnet and I wouldn't do it for wifi connected systems either.  NFS and wifi aren't a good pair, though people do use it that way.    The only answer I have is for you to make some test accounts and see how sharing HOME over NFS works across all the machines.

Samba is useful only for Windows clients. Don't use it for Linux clients when NFSv4 is a native, faster, more secure solution.

NTP can run anywhere on the network. I suspect they recommend running it on the DNS/DHCP box just because none of those services is really heavy. Doesn't matter.

Have you looked at **FreeIPA**?  I suspect that would be the best option for your career.

I haven't run this stuffwith LDAP in about 4 yrs and never attempted FreeIPA because it wasn't ported to Debian/Ubuntu at the time. There are packages for 16.04.


IMHO.

---

