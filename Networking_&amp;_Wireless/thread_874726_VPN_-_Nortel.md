---
title: "VPN - Nortel"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by petermoffat on 2008-07-30
I've read some threads on the forum about using vpnc-nortel branch to connect to vpn, but I've had no luck getting it anywhere near installing, never mind running.

The thread that looks the most promising[1] was posted in 2007 some time, does the fact that no one else is having problems mean there is some other way to do this now?

I've seen that novell supports nortel[2] in suse, any chance that will work? 

Running Ubuntu Hardy/XP atm, would really like all my harddrive space for one OS!!

[1]http://ubuntuforums.org/showthread.php?t=441042&highlight=nortel
[2]http://www.novell.com/coolsolutions/feature/18321.html

---

### Post by ir0nman on 2008-08-11
I would be interested in this too as my work uses Nortel, and while they provide the Nortel client it doesn't work on HH.

Thanks!
-Rick

---

### Post by n5nx on 2008-12-04
I too tried things in that thread... I was able to compile and install the code, but I cannot get around the requirement for the group ID and secret code. We don't use those, and I know we don't use them because I also managed to get the Apani client compiled and working. That required a license, but it worked, and I never had to give it a groupID or secret code....

Really hope vpnc nortel branch can be made to work without group ID and secret code when those are not used.

---

### Post by tpurch on 2008-12-12
I have downloaded vpnc nortel branch and compiled it, I am using Kubuntu 8.10.  

After a couple of issues I have managed to get it working and am now able to connect to work without issue.

 this is what I did:

sudo bash
cd vpnc-nortel
make
make install
edited /etc/vpnc/default.conf
added the following lines:

Vendor nortel    # note without this you get INVALID_EXCHANGE_TYPE 7 error
IPSec gateway <gateway>
IPSec ID <group-id>
IPSec secret <group-psk>
Xauth username <username>

vpnc 

when asked for my password, I typed my 4 digit pin and 6 digit passcode from secureID for example 1234123456

connection failed.....reporting I needed to use --enable-1des option, so tried again:

vpnc --enable-ldes

vpn connected, but routing and dns didn't work.

I tried some manual entries to resolv.conf & routing tables and was able to access works intanet.  

I decided rather than run command line scripts to bring up the connection and fix routing/dns problems.  I would be nice to connect via gui, so I tried Kvpnc.

I setup a Kvpnc profile, made changes for cisco vpnc settings.  re-pointed Kvpnc (free cisco /usr/sbin/vpnc to /usr/local/sbin/vpnc).  Kvpnc was failing with INVALID_EXCHANGE_TYPE error.  I noticed that the command executed to vpnc was specifying what options to use rather than reading /etc/vpnc/default.conf and I couldn't find a way to modify the line parameters for vpnc in Kvpnc config to because I needed to add --vendor nortel, so I went back to the orginal vpnc source code, edited config.c and changed

static const char *config_def_vendor(void)
{
        return "cisco";
}

to static const char *config_def_vendor(void)
{
        return "nortel";
}

then re-compiled & installed:

sudo bash
make
make install


Kvpnc now works!!!! all DNS and Routing works and when I disconnect VPN the DNS and routing reverts to orginal settings. :)

I hope this helps people with configuring nortel vpnc!

---

### Post by tpurch on 2008-12-12
> **n5nx said:**
> I too tried things in that thread... I was able to compile and install the code, but I cannot get around the requirement for the group ID and secret code. We don't use those, and I know we don't use them because I also managed to get the Apani client compiled and working. That required a license, but it worked, and I never had to give it a groupID or secret code....

Really hope vpnc nortel branch can be made to work without group ID and secret code when those are not used.

maybe a silly question, but what happens if you leave them blank?

---

### Post by ubulex on 2009-01-02
Thank you very much **tpurch** great howto :D
You helped me setting up a working VPN connection to a Nortel Contivity VPN with Ubuntu 8.04 Hardy Heron using vpnc-nortel with comfortable KVpnc GUI

---

### Post by artships on 2009-01-08
I got mine to work, too.  Had fetch and compile the latest vpnc-nortel:

```
svn co http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/  
cd vpnc-nortel
make
```

Copied the included vpnc-script to /etc/vpnc/custom-script because that's where I said it would be in /etc/vpnc.conf

Created /etc/vpnc.conf as:
```
IPSec gateway address.of.company.VPNgateway
IPSec ID in_my_case_the_company_name
IPSec the_secret_id
Enable Single DES
Xauth username my_company_username
IKE DH Group dh1
Vendor nortel
Script /etc/vpnc/custom-script
DPD idle timeout (our side) 18000
No Detach
Nortel Client ID V05_01
```
Most of these values I got from the ini file in the company's Windows Nortel Contivity client.

Executing vpnc now lets me in to my company's network.  Before I could
```
ssh -X my_company_username@sunos.server.address
``` I had to fix my .cshrc file on  sunos.server.address to NOT change the $DISPLAY variable to the gateway, but let it set $DISPLAY to localhost:10.0.

The only thing I haven't managed yet is "masquerading" - using Firefox on my ubuntu system to access company-local websites through the vpnc and internet websites without going through the my company.

---

### Post by Gibby13 on 2010-05-28
I got vpnc from the command line working on 10.04. Was trying kvpnc and getting weird errors. I changed the config.c like you said and now I am getting Port Binding failed, any help?

---

