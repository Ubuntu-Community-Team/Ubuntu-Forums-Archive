---
title: "Setting up a Samba AD DC on Ubuntu 20.04 LTS advice/instructions"
date: 2021-02-08
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2021-02-08
I'm about to embark on installing a new SAMBA AD DC server on Ubuntu 20.04. 

This is in anticipation of future removal of NT style Domains from Samba. Its something I've been putting off for years. 

Can anyone direct me to a Ubuntu 20.04 tutorial or cook book for accomplishing this task? 
Installing samba is easy - configuring it seems complicated and I'm not familiar with most of the necessary components.
I'm a little surprised someone hasn't built a tool for configuring it, although given the variations between different version of Linux it would not be a trivial task.  
I've found several on the internet including generic ones from the SAMBA Team and some written by individuals around the internet. 
The Samba Team ones seem to be generic Linux and not Ubuntu Specific. 
All of the individual ones seem full of editorial comments and personal preferences.

I'm more interested in simplicity than perfection.

---

### Post by hortimech1 on 2021-02-09
Try this:

#
# Set up a Samba AD DC on Ubuntu 20.04 server
#
 
login to a freshly installed and fully updated Ubuntu 20.04 computer

Assumptions:

your Ubuntu 20.04 computer:

Has a fixed IP: 192.168.0.223
Gateway: 192.168.0.1      
Nameserver: 8.8.8.8          
Hostname: u2004dc
Dns domain name: example.com
Realm: EXAMPLE.COM
Workgroup: EXAMPLE

sudo nano /etc/hosts

Change:

127.0.1.1 u2004dc

To:

127.0.1.1 u2004dc.example.com u2004dc

---------------------

The following commands should produce output like this

adminuser@u2004dc:~$ hostname -s
u2004dc
adminuser@u2004dc:~$ hostname -d
example.com
adminuser@u2004dc:~$ hostname -f
u2004dc.example.com
adminuser@u2004dc:~$ hostname -i
127.0.1.1
adminuser@u2004dc:~$ hostname -I
192.168.0.223 

Install the required packages:

sudo apt install acl attr samba winbind ntp binutils ldb-tools krb5-user -y

Press the 'Enter' key when prompted.

Stop the Samba daemons and disable them:

sudo systemctl stop nmbd smbd winbind
sudo systemctl disable nmbd smbd winbind
sudo systemctl mask nmbd smbd winbind

Unmask the 'Samba' daemon and enable it:

sudo systemctl unmask samba-ad-dc
sudo systemctl enable samba-ad-dc

---------------------

Setup NTP:

sudo cp /etc/ntp.conf{,.backup}

sudo nano /etc/ntp.conf

Make it look like this:

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift

# Leap seconds definition provided by tzdata
leapfile /usr/share/zoneinfo/leap-seconds.list

# Location of the samba ntp_signed directory
ntpsigndsocket /var/lib/samba/ntp_signd

# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

# Specify one or more NTP servers.

# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See [http://www.pool.ntp.org/join.html](http://www.pool.ntp.org/join.html) for
# more information.
pool 0.ubuntu.pool.ntp.org iburst
pool 1.ubuntu.pool.ntp.org iburst
pool 2.ubuntu.pool.ntp.org iburst
pool 3.ubuntu.pool.ntp.org iburst

# Use Ubuntu's ntp server as a fallback.
pool ntp.ubuntu.com

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery limited mssntp
restrict -6 default kod notrap nomodify nopeer noquery limited mssntp

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Needed for adding pool entries
restrict source notrap nomodify noquery

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

Restart 'ntp':

sudo systemctl restart ntp

---------------------

Setup Samba as an AD DC:.
 
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.orig

In the following provision command, replace 'xxxxxxxxxxxx' with a complex password

sudo samba-tool domain provision --use-rfc2307 --realm=EXAMPLE.COM --domain=EXAMPLE --adminpass=xxxxxxxxxxxx

INFO 2021-02-09 11:42:02,181 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #2128: Looking up IPv4 addresses
[snipped for brevity]
..........
INFO 2021-02-09 11:43:02,605 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #2394: A Kerberos configuration suitable for Samba AD has been generated at /var/lib/samba/private/krb5.conf
INFO 2021-02-09 11:43:02,607 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #2396: Merge the contents of this file with your system krb5.conf or replace it with this one. Do not create a symlink!
INFO 2021-02-09 11:43:03,607 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #2102: Setting up fake yp server settings
INFO 2021-02-09 11:43:05,415 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #490: Once the above files are installed, your Samba AD server will be ready to use
INFO 2021-02-09 11:43:05,416 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #495: Server Role:           active directory domain controller
INFO 2021-02-09 11:43:05,418 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #496: Hostname:              u2004dc
INFO 2021-02-09 11:43:05,419 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #497: NetBIOS Domain:        EXAMPLE
INFO 2021-02-09 11:43:05,419 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #498: DNS Domain:            example.com
INFO 2021-02-09 11:43:05,420 pid:3445 /usr/lib/python3/dist-packages/samba/provision/__init__.py #499: DOMAIN SID:            S-1-5-21-3824328586-2680838998-4094433204

sudo cp /etc/krb5.conf /etc/krb5.conf.orig

sudo cp /var/lib/samba/private/krb5.conf /etc/krb5.conf

Set apparmor to allow ntp access to its Samba socket

sudo nano /etc/apparmor.d/local/usr.sbin.ntpd

# To sign replies to MS-SNTP clients by the NTP daemon in /var/lib/samba
/var/lib/samba/ntp_signd/socket rw,

Correct resolving:

sudo systemctl stop systemd-resolved.service
sudo systemctl mask systemd-resolved.service
sudo rm /etc/resolv.conf

sudo nano /etc/resolv.conf

nameserver 192.168.0.223
search example.com

Fix the dns forwarder in smb.conf:

sudo sed -i 's/127.0.0.53/8.8.8.8/' /etc/samba/smb.conf

Start Samba:

sudo systemctl start samba-ad-dc

Now create the dns reversezone and then add a reverse record for the DC. When prompted for a password, enter the one used during the provision.

sudo samba-tool dns zonecreate u2004dc 0.168.192.in-addr.arpa -U Administrator

sudo samba-tool dns add u2004dc 0.168.192.in-addr.arpa 223 PTR u2004dc.example.com -U Administrator

Display AD users:

wbinfo -u
EXAMPLE\administrator
EXAMPLE\guest
EXAMPLE\krbtgt

Display AD groups:

wbinfo -g
EXAMPLE\cert publishers
EXAMPLE\ras and ias servers
EXAMPLE\allowed rodc password replication group
EXAMPLE\denied rodc password replication group
EXAMPLE\dnsadmins
EXAMPLE\enterprise read-only domain controllers
EXAMPLE\domain admins
EXAMPLE\domain users
EXAMPLE\domain guests
EXAMPLE\domain computers
EXAMPLE\domain controllers
EXAMPLE\schema admins
EXAMPLE\enterprise admins
EXAMPLE\group policy creator owners
EXAMPLE\read-only domain controllers
EXAMPLE\dnsupdateproxy

You should now have a working Samba AD DC

---

### Post by rsteinmetz70112 on 2021-02-12
Thanks for the detailed instructions. I worked almost perfectly and was a lot more Ubuntu centric than any of the other guides I found. 

I've got the samba stuff running but I do have a problem. It appears DNS is not quite working. I used our domain name for the realm but I also have other servers using that domain located in other locations which I cannot reach. I can reach other domains. Other computers on the network haven't been added to the domain yet but can still reach these other computers.

---

### Post by rsteinmetz70112 on 2021-02-14
OK I've got a solution to my DNS problem but 

I've discovered that /etc/resolv.conf is being rewritten whenever I reboot.
```
sudo chattr +i /etc/resolv.conf
```
samba-ac-dc is not starting on reboot
```
sudo systemctl enable samba-ad-dc
sudo systemctl start samba-ad-dc
```
I needed to set up winbindd and:
```
$sudo  vi /etc/nsswitch.conf
passwd:         compat winbind systemd
group:          compat winbind systemd
shadow:         compat winbind
```
I also discovered I need to install :
```
sudo app install libpam-winbind libnss-winbind libpam-krb5 
```
I think I have a fully functioning domain controller now. 
Still testing and configuring.

---

