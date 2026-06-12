---
title: "Syslog-NG Messages received but not wirtten to file"
date: 2017-02-15
forum: Networking &amp; Wireless
---

### Post by thebob2 on 2017-02-15
Dear all,

i have problem with syslog-ng because I received the message but nothing is written to file. Hier my data:
syslog-ng version: 3.5
Ubuntu: 16.04 Server

I see all data comming via tcpdump:
> 
11:34:05.719352 IP 192.168.174.155.58964 > 192.168.168.122.514: SYSLOG local7.warning, length: 140
11:34:06.102362 IP 192.168.174.154.53230 > 192.168.168.122.514: SYSLOG local7.warning, length: 141


Config files located on /etc/syslog-ng/conf.d
example 1:
> 
#### Cisco Access Switch
source p-dls3_udp {
    udp(port(514));
 };
destination d-dls3 {
    file("/var/log/c-switch/dls3.log");
#  owner(root) group(users) perm(0640));
 };
filter f-dls3 {
    host("192.168.174.154");
 };
log {
    source(p-dls3_udp);
    filter(f-dls3);
    destination(d-dls3);
 };


exampel 2:
> 
###Cisco Access Switch
source p-dls4_udp {
    udp(port(514));
 };
destination d-dls4 {
    file("/var/log/c-switch/dls4.log");
#  owner(root) group(users) perm(0640));
 };
filter f-dls4 {
    host("192.168.174.155");
 };
log {
    source(p-dls4_udp);
    filter(f-dls4);
    destination(d-dls4);
 };


Files located in /var/log/c-switch/
```

u012001@ubu-trz-term-1:/var/log/c-switch$ ls -la
total 16
drwxr-xr-x  2 root root   4096 Feb 15 13:11 .
drwxr-xr-x 18 root syslog 4096 Feb 15 07:36 ..
-rw-r-----  1 root root      0 Feb 14 13:51 cls1.log
-rw-r-----  1 root root      0 Feb 14 13:51 dls1.log
-rw-r-----  1 root root      0 Feb 14 13:51 dls2.log
-rw-r-----  1 root root      0 Feb 14 13:51 dls3.log
-rw-r-----  1 root root      0 Feb 14 13:51 dls4.log
-rw-r-----  1 root root      0 Feb 14 13:51 dls5.log

```

Any idear why i don't get any messeages written in files?

Thank you very much.
wrbrgds
TheTBC

---

### Post by fekete77-robert on 2017-02-16
Hi, 

Try if it works without the filters, or run syslog-ng in the foreground (syslog-ng -Fevd) to see if it shows an error or other related message.

AFAIK, if you have name resolving or keep-hostname enabled in syslog-ng,  then the host() filter refers to the hostname, not the IP address, so  I'd suspect that using host("hostname ") in your filters (or netmask(192.168.174.154/24) instead of the host() filter) will solve the problem.

Regards, 
Robert

---

### Post by thebob2 on 2017-02-16
Hi Robert,

thank for relpy.
I have checked the configuration without filter and with filter (netmask). In both cases i didn't get any file Messages.
here my both examples:
> 
###Cisco Core Switch trzicls2
source p-cls2_udp {
     udp(port(514));
 };
destination d-cls2 {
     file(/var/log/c-switch/cls2.log);
 };
filter f-cls2 {
     netmask("192.168.168.2/24");
 };
log {
    source(p-cls2_udp);
    filter(f-cls2);
    destination(d-cls2);
 };

and
> 
###Cisco Core Switch trzicls2
source p-cls2_udp {
     udp(port(514));
 };
destination d-cls2 {
     file(/var/log/c-switch/cls2.log);
#  owner(root) group(users) perm(0640));
 };
# filter f-cls2 {
#     netmask("192.168.168.2/24");
 #};
log {
    source(p-cls2_udp);
    # filter(f-cls2);
    destination(d-cls2);
 };


Restart of service for each config change.
And here again the tcpdump:
> 
12:35:02.430387 IP 192.168.168.2.55764 > 192.168.168.122.514: SYSLOG local7.warning, length: 300
12:38:32.739373 IP 192.168.168.2.55764 > 192.168.168.122.514: SYSLOG local7.critical, length: 92
12:41:12.662556 IP 192.168.168.2.55764 > 192.168.168.122.514: SYSLOG local7.critical, length: 92
12:47:31.172584 IP 192.168.168.2.55764 > 192.168.168.122.514: SYSLOG local7.warning, length: 320
12:59:50.131062 IP 192.168.168.2.55764 > 192.168.168.122.514: SYSLOG local7.warning, length: 321
13:00:40.430573 IP 192.168.168.2.55764 > 192.168.168.122.514: SYSLOG local7.critical, length: 94
13:02:59.847128 IP 192.168.168.2.60125 > 192.168.168.122.514: SYSLOG local7.notice, length: 115
13:03:04.851593 IP 192.168.168.2.60125 > 192.168.168.122.514: SYSLOG local7.info, length: 132
13:03:05.850947 IP 192.168.168.2.60125 > 192.168.168.122.514: SYSLOG local7.info, length: 132
13:04:13.297691 IP 192.168.168.2.60125 > 192.168.168.122.514: SYSLOG local7.notice, length: 115
13:10:41.357370 IP 192.168.168.2.60125 > 192.168.168.122.514: SYSLOG local7.warning, length: 320


Config of Syslog-NG
> 
# First, set some global options.
options { chain_hostnames(off); flush_lines(0); use_dns(no); use_fqdn(no);
          owner("root"); group("adm"); perm(0640); stats_freq(0);
          bad_hostname("^gconfd$");
};


Syslog Messeges:
> 
u012001@ubu-trz-term-1:/etc/syslog-ng$ syslog-ng -Fevd
syslog-ng: Error setting capabilities, capability management disabled; error='Operation not permitted'
Starting to read include file; filename='/etc/syslog-ng/scl.conf', depth='1'
Global value changed; define='scl-root', value='/usr/share/syslog-ng/include/scl'
Global value changed; define='include-path', value='/etc/syslog-ng:/usr/share/syslog-ng/include'
Starting to read include file; filename='/usr/share/syslog-ng/include/scl/system/plugin.conf', depth='2'
Module loaded and initialized successfully; module='system-source'
Finishing include; filename='/usr/share/syslog-ng/include/scl/system/plugin.conf', depth='2'
Starting to read include file; filename='/usr/share/syslog-ng/include/scl/pacct/plugin.conf', depth='2'
Reading path for candidate modules; path='/usr/lib/syslog-ng/3.5.6'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afstomp.so', module='afstomp'
Registering candidate plugin; module='afstomp', context='destination', name='stomp', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='tfgeoip.so', module='tfgeoip'
Registering candidate plugin; module='tfgeoip', context='template-func', name='geoip', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afuser.so', module='afuser'
Registering candidate plugin; module='afuser', context='destination', name='usertty', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afsmtp.so', module='afsmtp'
Registering candidate plugin; module='afsmtp', context='destination', name='smtp', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='confgen.so', module='confgen'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afsocket-notls.so', module='afsocket-notls'
Registering candidate plugin; module='afsocket-notls', context='source', name='unix-stream', preference='0'
Registering candidate plugin; module='afsocket-notls', context='destination', name='unix-stream', preference='0'
Registering candidate plugin; module='afsocket-notls', context='source', name='unix-dgram', preference='0'
Registering candidate plugin; module='afsocket-notls', context='destination', name='unix-dgram', preference='0'
Registering candidate plugin; module='afsocket-notls', context='source', name='tcp', preference='0'
Registering candidate plugin; module='afsocket-notls', context='destination', name='tcp', preference='0'
Registering candidate plugin; module='afsocket-notls', context='source', name='tcp6', preference='0'
Registering candidate plugin; module='afsocket-notls', context='destination', name='tcp6', preference='0'
Registering candidate plugin; module='afsocket-notls', context='source', name='udp', preference='0'
Registering candidate plugin; module='afsocket-notls', context='destination', name='udp', preference='0'
Registering candidate plugin; module='afsocket-notls', context='source', name='udp6', preference='0'
Registering candidate plugin; module='afsocket-notls', context='destination', name='udp6', preference='0'
Registering candidate plugin; module='afsocket-notls', context='source', name='syslog', preference='0'
Registering candidate plugin; module='afsocket-notls', context='destination', name='syslog', preference='0'
Registering candidate plugin; module='afsocket-notls', context='source', name='network', preference='0'
Registering candidate plugin; module='afsocket-notls', context='destination', name='network', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afprog.so', module='afprog'
Registering candidate plugin; module='afprog', context='source', name='program', preference='0'
Registering candidate plugin; module='afprog', context='destination', name='program', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='basicfuncs.so', module='basicfuncs'
Registering candidate plugin; module='basicfuncs', context='template-func', name='grep', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='if', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='echo', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='length', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='substr', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='strip', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='sanitize', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='lowercase', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='uppercase', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='replace-delimiter', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='+', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='-', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='*', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='/', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='%', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='ipv4-to-int', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='indent-multi-line', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='context-length', preference='0'
Registering candidate plugin; module='basicfuncs', context='template-func', name='env', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='json-plugin.so', module='json-plugin'
Registering candidate plugin; module='json-plugin', context='parser', name='json-parser', preference='0'
Registering candidate plugin; module='json-plugin', context='template-func', name='format_json', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='affile.so', module='affile'
Registering candidate plugin; module='affile', context='source', name='file', preference='0'
Registering candidate plugin; module='affile', context='source', name='pipe', preference='0'
Registering candidate plugin; module='affile', context='destination', name='file', preference='0'
Registering candidate plugin; module='affile', context='destination', name='pipe', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='dbparser.so', module='dbparser'
Registering candidate plugin; module='dbparser', context='parser', name='db-parser', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='syslog-ng-crypto.so', module='syslog-ng-crypto'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afsocket.so', module='afsocket'
Registering candidate plugin; module='afsocket', context='source', name='unix-stream', preference='100'
Registering candidate plugin; module='afsocket', context='destination', name='unix-stream', preference='100'
Registering candidate plugin; module='afsocket', context='source', name='unix-dgram', preference='100'
Registering candidate plugin; module='afsocket', context='destination', name='unix-dgram', preference='100'
Registering candidate plugin; module='afsocket', context='source', name='tcp', preference='100'
Registering candidate plugin; module='afsocket', context='destination', name='tcp', preference='100'
Registering candidate plugin; module='afsocket', context='source', name='tcp6', preference='100'
Registering candidate plugin; module='afsocket', context='destination', name='tcp6', preference='100'
Registering candidate plugin; module='afsocket', context='source', name='udp', preference='100'
Registering candidate plugin; module='afsocket', context='destination', name='udp', preference='100'
Registering candidate plugin; module='afsocket', context='source', name='udp6', preference='100'
Registering candidate plugin; module='afsocket', context='destination', name='udp6', preference='100'
Registering candidate plugin; module='afsocket', context='source', name='syslog', preference='100'
Registering candidate plugin; module='afsocket', context='destination', name='syslog', preference='100'
Registering candidate plugin; module='afsocket', context='source', name='network', preference='100'
Registering candidate plugin; module='afsocket', context='destination', name='network', preference='100'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afsql.so', module='afsql'
Registering candidate plugin; module='afsql', context='destination', name='sql', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='cryptofuncs.so', module='cryptofuncs'
Registering candidate plugin; module='cryptofuncs', context='template-func', name='uuid', preference='0'
Registering candidate plugin; module='cryptofuncs', context='template-func', name='hash', preference='0'
Registering candidate plugin; module='cryptofuncs', context='template-func', name='sha1', preference='0'
Registering candidate plugin; module='cryptofuncs', context='template-func', name='sha256', preference='0'
Registering candidate plugin; module='cryptofuncs', context='template-func', name='sha512', preference='0'
Registering candidate plugin; module='cryptofuncs', context='template-func', name='md4', preference='0'
Registering candidate plugin; module='cryptofuncs', context='template-func', name='md5', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='redis.so', module='redis'
Registering candidate plugin; module='redis', context='destination', name='redis', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='syslogformat.so', module='syslogformat'
Registering candidate plugin; module='syslogformat', context='format', name='syslog', preference='0'
Registering candidate plugin; module='syslogformat', context='parser', name='syslog-parser', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afsocket-tls.so', module='afsocket-tls'
Registering candidate plugin; module='afsocket-tls', context='source', name='unix-stream', preference='100'
Registering candidate plugin; module='afsocket-tls', context='destination', name='unix-stream', preference='100'
Registering candidate plugin; module='afsocket-tls', context='source', name='unix-dgram', preference='100'
Registering candidate plugin; module='afsocket-tls', context='destination', name='unix-dgram', preference='100'
Registering candidate plugin; module='afsocket-tls', context='source', name='tcp', preference='100'
Registering candidate plugin; module='afsocket-tls', context='destination', name='tcp', preference='100'
Registering candidate plugin; module='afsocket-tls', context='source', name='tcp6', preference='100'
Registering candidate plugin; module='afsocket-tls', context='destination', name='tcp6', preference='100'
Registering candidate plugin; module='afsocket-tls', context='source', name='udp', preference='100'
Registering candidate plugin; module='afsocket-tls', context='destination', name='udp', preference='100'
Registering candidate plugin; module='afsocket-tls', context='source', name='udp6', preference='100'
Registering candidate plugin; module='afsocket-tls', context='destination', name='udp6', preference='100'
Registering candidate plugin; module='afsocket-tls', context='source', name='syslog', preference='100'
Registering candidate plugin; module='afsocket-tls', context='destination', name='syslog', preference='100'
Registering candidate plugin; module='afsocket-tls', context='source', name='network', preference='100'
Registering candidate plugin; module='afsocket-tls', context='destination', name='network', preference='100'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afamqp.so', module='afamqp'
Registering candidate plugin; module='afamqp', context='destination', name='amqp', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='linux-kmsg-format.so', module='linux-kmsg-format'
Registering candidate plugin; module='linux-kmsg-format', context='format', name='linux-kmsg', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='system-source.so', module='system-source'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='afmongodb.so', module='afmongodb'
Registering candidate plugin; module='afmongodb', context='destination', name='mongodb', preference='0'
Reading shared object for a candidate module; path='/usr/lib/syslog-ng/3.5.6', fname='csvparser.so', module='csvparser'
Registering candidate plugin; module='csvparser', context='parser', name='csv-parser', preference='0'
Finishing include; filename='/usr/share/syslog-ng/include/scl/pacct/plugin.conf', depth='2'
Starting to read include file; filename='/usr/share/syslog-ng/include/scl/syslogconf/plugin.conf', depth='2'
Module loaded and initialized successfully; module='confgen'
Finishing include; filename='/usr/share/syslog-ng/include/scl/syslogconf/plugin.conf', depth='2'
Finishing include; filename='/etc/syslog-ng/scl.conf', depth='1'
Starting to read include file; filename='/usr/share/syslog-ng/include/scl/system/tty10.conf', depth='1'
Global value changed; define='tty10', value='/dev/tty10'
Finishing include; filename='/usr/share/syslog-ng/include/scl/system/tty10.conf', depth='1'
Module loaded and initialized successfully; module='afsocket'
Module loaded and initialized successfully; module='affile'
Finishing include; content='source confgen system', depth='1'
Module loaded and initialized successfully; module='afuser'
Adding include file; filename='/etc/syslog-ng/conf.d/cls1.conf'
Adding include file; filename='/etc/syslog-ng/conf.d/cls2.conf'
Adding include file; filename='/etc/syslog-ng/conf.d/dls1.conf'
Adding include file; filename='/etc/syslog-ng/conf.d/dls2.conf'
Adding include file; filename='/etc/syslog-ng/conf.d/dls3.conf'
Adding include file; filename='/etc/syslog-ng/conf.d/dls4.conf'
Adding include file; filename='/etc/syslog-ng/conf.d/dls6.conf'
Adding include file; filename='/etc/syslog-ng/conf.d/test.conf'
Adding include file; filename='/etc/syslog-ng/conf.d/ttrgnas2.conf'
Starting to read include file; filename='/etc/syslog-ng/conf.d/cls1.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/cls1.conf', depth='1'
Starting to read include file; filename='/etc/syslog-ng/conf.d/cls2.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/cls2.conf', depth='1'
Starting to read include file; filename='/etc/syslog-ng/conf.d/dls1.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/dls1.conf', depth='1'
Starting to read include file; filename='/etc/syslog-ng/conf.d/dls2.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/dls2.conf', depth='1'
Starting to read include file; filename='/etc/syslog-ng/conf.d/dls3.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/dls3.conf', depth='1'
Starting to read include file; filename='/etc/syslog-ng/conf.d/dls4.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/dls4.conf', depth='1'
Starting to read include file; filename='/etc/syslog-ng/conf.d/dls6.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/dls6.conf', depth='1'
Starting to read include file; filename='/etc/syslog-ng/conf.d/test.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/test.conf', depth='1'
Starting to read include file; filename='/etc/syslog-ng/conf.d/ttrgnas2.conf', depth='1'
Finishing include; filename='/etc/syslog-ng/conf.d/ttrgnas2.conf', depth='1'
Error creating persistent state file; filename='/var/lib/syslog-ng/syslog-ng.persist-', error='Permission denied (13)'
u012001@ubu-trz-term-1:/etc/syslog-ng$


any other idear?

regards TBC

---

### Post by fekete77-robert on 2017-02-17
Are the errors from the first and last lines there when you run 'syslog-ng -Fevd' as root? Do you have Apparmor/Selinux running that might limit where syslog-ng can write files?

---

### Post by thebob2 on 2017-02-20
Hi [**[COLOR=#000000]fekete77-robert[/COLOR]**]("https://ubuntuforums.org/member.php?u=2059097")

it shoud be realy a problem of limititation of more the one file. I have now 1 file without filter and i get log files.

I don't know about Apparmor/Selinux but have found this both paramters and output:

> 
u012001@ubu-trz-term-1:/var/log/c-switch$ selinuxenabled && echo enabled || echo disabled
The program 'selinuxenabled' is currently not installed. To run 'selinuxenabled' please ask your administrator to install the package 'selinux-utils'
disabled


> 
u012001@ubu-trz-term-1:/var/log/c-switch$ sudo apparmor_status
apparmor module is loaded.
22 profiles are loaded.
21 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/lxc-start
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/lxd/lxd-bridge-proxy
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ippusbxd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
   lxc-container-default
   lxc-container-default-cgns
   lxc-container-default-with-mounting
   lxc-container-default-with-nesting
1 profiles are in complain mode.
   /usr/sbin/sssd
6 processes have profiles defined.
2 processes are in enforce mode.
   /usr/sbin/cups-browsed (29763)
   /usr/sbin/ntpd (1936)
4 processes are in complain mode.
   /usr/sbin/sssd (1821)
   /usr/sbin/sssd (1876)
   /usr/sbin/sssd (2008)
   /usr/sbin/sssd (2009)
0 processes are unconfined but have a profile defined.


Is there something what I need to change to get Logiles with more than one config file?
Thank you all for helping.

wbrgrds

TBC

---

### Post by fekete77-robert on 2017-02-20
Hi, 

if it is working without the filters, then I'd suspect that the filters are not working properly, possibly because the incoming messages are not fully syslog-compliant, and the host field does not contain what it should. 
To check if this is the problem, you can add a new logpath that processes every message, and writes the value of the HOST field into a file, something like:

[COLOR=#000000]destination d_file [/COLOR][COLOR=#666600]{[/COLOR][COLOR=#000000]
    file [/COLOR][COLOR=#666600]([/COLOR][COLOR=#008800]"/var/log/test.log"[/COLOR][COLOR=#000088]template[/COLOR][COLOR=#666600]([/COLOR][COLOR=#008800]"${ISODATE} ${HOST}\n"[/COLOR][COLOR=#666600])[/COLOR][COLOR=#666600]);[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#666600]};[/COLOR][COLOR=#000000]

log [/COLOR][COLOR=#666600]{[/COLOR][COLOR=#000000] source(p-cls2_udp); source(p-dls2_udp);[/COLOR][COLOR=#000000] destination[/COLOR][COLOR=#666600]([/COLOR][COLOR=#000000]d_file[/COLOR][COLOR=#666600]);[/COLOR][COLOR=#000000] flags[/COLOR][COLOR=#666600]([/COLOR][COLOR=#000000]catchall[/COLOR][COLOR=#666600]);[/COLOR][COLOR=#666600]};[/COLOR]

---

### Post by thebob2 on 2017-02-22
Hi Robert,

we have now fixed the problem as followed:
generate a conf file like switch.conf under:/etc/syslog-ng/conf.d/
> 
### Script to get logs from switches
source s_me { udp(ip(192.168.xxx.yyy) port (514)); };  ###IP Addr. from Syslog Server

destination d_cls1 { file("/var/log/c-switch/cls1.log"); }; 
destination d_dls1 { file("/var/log/c-switch/dls1.log"); };
destination d_dall { file("/var/log/c-switch/dall.log"); };

filter f_cls1 { netmask(192.168.xxx.1/32);   };   ###IP Addr. form Switch 1 as Netmask declaration
filter f_dls1 { netmask(192.168.yyy.152/32); };   ###IP Addr. form Switch 2 as Netmask declaration
filter f_netm { netmask(192.168.0.0/16); };       ###IP Range. form Network as Netmask declaration

log { source( s_me ); filter( f_cls1 ); destination( d_cls1 ); };
log { source( s_me ); filter( f_dls1 ); destination( d_dls1 ); };
log { source( s_me ); filter( f_netm ); destination( d_dall ); };


and then you will received für each device a separate logfile under /var/log/c-switch/ or what you specified.

Thanks for all your help!

---

