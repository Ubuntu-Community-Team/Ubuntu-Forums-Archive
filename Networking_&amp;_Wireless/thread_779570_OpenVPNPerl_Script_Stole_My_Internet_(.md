---
title: "OpenVPN/Perl Script Stole My Internet? :("
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by laeg_ on 2008-05-02
I installed OpenVPN via synaptic package manager along with the files it recommended accompany it and then used the following commands as per my new provider's instructions:

```
sudo mkdir /etc/openvpn (this deleted a file that was in the pre-existing openvpn dir)
cp torrentfreedom.pl /etc/openvpn
cd /etc/openvpn
perl torrentfreedom.pl laeg <mypass>
```

The output from the last command was:

```
--21:27:33--  https://www.torrentfreedom.com/scripts/version.php?username=laeg&<mypass>
          => `/dev/null'
Resolving www.torrentfreedom.com... my.ip.address
Connecting to www.torrentfreedom.com|my.ip.address|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
21:27:38 ERROR 404: Not Found.

laeg.conf: Permission denied
ca.crt: Permission denied
laeg.crt: Permission denied
laeg.key: Permission denied
Options error: In [CMD-LINE]:1: Error opening configuration file: laeg.conf
Use --help for more information.
```

I tried this several times. The contents of of torrentfreedom.pl:

```
#!/usr/bin/perl
use strict;

# torrentfreedom perl client
# v1.1

# initiates and manages a connection to TorrentFreedom without using a GUI.

# set additional proxy settings here - check out openvpn.net's manpage for options.
# eg: my $additional_options = "--http-proxy 11.22.33.44 8080";
# to tell the client to use a http proxy.
my $additional_options = "";

my $username = shift;
my $password = shift;

if (length($username) < 1 || length($password) < 1)
{
	# poke user if they didn't enter a username or password
	print "usage: perl torrentfreedom.pl [username] [password]\n";
	exit;
}

# report version - used for stats and update notifications 
my $argstream1 = "https://www.torrentfreedom.com/scripts/version.php?username=$username&password=$password";
my $argstream2 = "--output-document=/dev/null";
system("wget",$argstream1,$argstream2);

# get config file
$argstream1 = "https://www.torrentfreedom.com/scripts/config.php?username=$username&password=$password";
$argstream2 = "--output-document=$username.conf";
system("wget",$argstream1,$argstream2);

# get CA
$argstream1 = "https://www.torrentfreedom.com/scripts/ca.php?username=$username&password=$password";
$argstream2 = "--output-document=ca.crt";
system("wget",$argstream1,$argstream2);

# get user's cert
$argstream1 = "https://www.torrentfreedom.com/scripts/usercrt.php?username=$username&password=$password";
$argstream2 = "--output-document=$username.crt";
system("wget",$argstream1,$argstream2);

# get user's key
$argstream1 = r along with the files it recommended to accompany it it and then used the following commands:
"https://www.torrentfreedom.com/scripts/userkey.php?username=$username&password=$password";
$argstream2 = "--output-document=$username.key";
system("wget",$argstream1,$argstream2);

# connect to openvpn - note, we never return from this - so the perl script basically ends here.
exec("openvpn --config $username.conf $additional_options") or print STDERR "couldn't run openvpn: $!";

# that's it.
```

I think I was still able to access webpages after this and before I restarted my box but I cannot be certain. Since restarting BitTorrent works but I cannot access any website in firefox and when I try to connect to a server in Irssi it returns "(cannot find service or name)". Also, when I bring up network manager everything under each of the tabs is greyed out so I can't change DNS or check my IP settings etc.

I have now deleted openvpn via synaptic package manager and manually removed the dir /etc/openvpn and the perl script inside it. I tried restarting but there was no change. I'm only able to surf and use IRC via the live cd. How can I remedy this?

---

### Post by laeg_ on 2008-05-03
I have my / and /home dirs on different partitions so if I do a reinstall and keep my /home dir will it resolve this?

---

