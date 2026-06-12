---
title: "file transfer fails from A -&gt; B"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by lumiad on 2008-03-04
Hi,

For about 2 days now I've been trying to transfer some files from computer A (gentoo) to computer B (kubuntu 7.10). Though every time I try the connection stalls.

I've been able to send a file from B -> A so it seems to be a configuration issue. Ip-tables is not installed (and no other firewall) so it can't be a firewall issue.

Does anyone know the solution to this?

_scp is used below but sftp and fish didn't work either_

From machine A -> B
*test@lumiad-desktop:~$ scp -rv lumiad@192.168.10.42:/home/lumiad/behaviournew_v2 behaviournew_v2/*
```

Executing: program /usr/bin/ssh host 192.168.10.42, user lumiad, command scp -v -r -f /home/lumiad/behaviournew_v2
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.10.42 [192.168.10.42] port 22.
debug1: Connection established.
debug1: identity file /home/test/.ssh/identity type -1
debug1: identity file /home/test/.ssh/id_rsa type -1
debug1: identity file /home/test/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7
debug1: match: OpenSSH_4.7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.10.42' is known and matches the RSA host key.
debug1: Found key in /home/test/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/test/.ssh/identity
debug1: Trying private key: /home/test/.ssh/id_rsa
debug1: Trying private key: /home/test/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password:
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: scp -v -r -f /home/lumiad/behaviournew_v2
Entering directory: D0755 0 behaviournew_v2
Sink: D0755 0 behaviournew_v2
Entering directory: D0755 0 doc
Sink: D0755 0 doc
Sending file modes: C0644 4566 notes-language
Sink: C0644 4566 notes-language
notes-language                                                                                                       0%    0     0.0KB/s - stalled -debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Killed by signal 2.
test@lumiad-desktop:~$

```

*cat ssh_config*
```

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

*cat sshd_config*
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

*lsmod*
```

Module                  Size  Used by
iptable_filter          3968  0
ip_tables              13924  1 iptable_filter
x_tables               16260  1 ip_tables
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0
cpufreq_userspace       5280  0
cpufreq_conservative     8072  0
cpufreq_ondemand        9612  0
cpufreq_powersave       2688  0
cpufreq_stats           7232  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
container               5504  0
ipv6                  273892  16
ac                      6148  0
button                  8976  0
video                  18060  0
sbs                    19592  0
dock                   10656  0
battery                11012  0
af_packet              24840  2
sbp2                   24072  0
lp                     12580  0
snd_intel8x0           34972  1
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
snd_rawmidi            25728  1 snd_seq_midi
usbhid                 29536  0
xpad                    9988  0
sis_agp                10116  0
hid                    28928  1 usbhid
k8temp                  6656  0
serio_raw               8068  0
psmouse                39952  0
pcspkr                  4224  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sis190                 22276  0
mii                     6528  1 sis190
amd64_agp              13700  1
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
agpgart                35016  2 sis_agp,amd64_agp
evdev                  11136  4
ext3                  133896  2
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
sd_mod                 30336  4
sata_sis                9988  0
ata_generic             8452  0
floppy                 60004  0
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0
ohci_hcd               22916  0
usbcore               138632  5 usbhid,xpad,ehci_hcd,ohci_hcd
pata_sis               15236  4 sata_sis
libata                125168  3 sata_sis,ata_generic,pata_sis
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor

```


ps -e | grep ssh
```

 4927 ?        00:00:00 ssh-agent
 5489 ?        00:00:00 sshd
 5491 ?        00:00:00 sshd
 5694 pts/4    00:00:00 ssh
 5699 pts/5    00:00:00 ssh
 6621 ?        00:00:00 sshd
 6623 ?        00:00:00 sshd
 6850 ?        00:00:00 sshd

```


Thanks!

---

### Post by doelman on 2008-03-05
It's solved by: [http://www.snailbook.com/faq/mtu-mismatch.auto.html](http://www.snailbook.com/faq/mtu-mismatch.auto.html)

---

