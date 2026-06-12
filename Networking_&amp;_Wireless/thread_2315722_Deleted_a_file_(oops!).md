---
title: "Deleted a file (oops!)"
date: 2016-03-01
forum: Networking &amp; Wireless
---

### Post by Veronica_Sanford on 2016-03-01
I was having trouble connecting to the wireless on my school laptop, so my professor sent directions on how I might fix the problem ([https://support.opendns.com/entries/38042814-Ubuntu](https://support.opendns.com/entries/38042814-Ubuntu)) . I mistakenly used the "rm" command and removed the file dhclient.conf (mentioned in step 8 of the instructions) which I presume is very important to making my internet work the way it's supposed to. Is there a way I can get it back or retrieve it from somewhere else?

---

### Post by Hadaka on 2016-03-01
Hi,please post the output of..
```
lsb_release -a
arch
```
*note ls is lowercase LS
Please post the output of..
```
cd /etc/dhcp
ls
```
then do```
cd
```
then post the output of..
```
cd /etc/dhcp3
ls
```
```
cd
```
thanks.

---

### Post by Veronica_Sanford on 2016-03-01
vesanford@vesanford-Latitude-3450:~$ lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

vesanford@vesanford-Latitude-3450:~$ arch
x86_64

vesanford@vesanford-Latitude-3450:~$ cd /etc/dhcp

vesanford@vesanford-Latitude-3450:/etc/dhcp$ ls
dhclient-enter-hooks.d  dhclient-exit-hooks.d

vesanford@vesanford-Latitude-3450:/etc/dhcp$ cd

vesanford@vesanford-Latitude-3450:~$ cd /etc/dhcp3
bash: cd: /etc/dhcp3: No such file or directory

vesanford@vesanford-Latitude-3450:~$ cd

---

### Post by SeijiSensei on 2016-03-02
I have a pretty vanilla configuration; my dhclient.conf looks like this:
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

#send host-name "andare.fugue.com";
send host-name = gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        dhcp6.name-servers, dhcp6.domain-search,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers,
        dhcp6.fqdn, dhcp6.sntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

As you can see most of it is commented out.  If we strip the comment lines with the command
```
grep -v '^\#' < /etc/dhcp/dhclient.conf
```
we are left with just the following:

```

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name = gethostname();
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        dhcp6.name-servers, dhcp6.domain-search,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers,
        dhcp6.fqdn, dhcp6.sntp-servers;

```

Try using that for starters and see how things go.

---

### Post by Veronica_Sanford on 2016-03-02
(I'm relatively new to using the command line, so I'm not exactly sure if what I'm about to say makes sense.) But I'm not able to use the command "grep" for the file dhclient.conf because it doesn't exist anymore since I deleted it. Is this true? Do I need to make the file first?
Thanks!

---

### Post by Hadaka on 2016-03-02
Hi, SeijiSensei is correct, once just the actual commands are stripped out there isnt much there.
you can copying that code then build the file by doing..
```
gksudo gedit /etc/dpkg/dhclient.conf
```
paste your copied code in then save and close.
to verify ,,,please do..
```
cat /etc/dchp/dhclient.conf
```
.....OR......
you can insert the usb you used to load 15.04..boot to it...click "Try Ubuntu"
then click the launcher then click *files >> computer >> etc >> dpkg*
then copy and save to a usb./cdrom or highlight the file click copy, exit the "Try Ubuntu"
mode,boot back into your regulat 15.04 and save it there same as above.
thanks.

---

### Post by SeijiSensei on 2016-03-02
From the command prompt, you can create the file like this:

```
sudo nano /etc/dhcp/dhclient.conf
```

That will open the nano editor.  Now paste the contents of the last block of code I gave above into the editor.  Hold down the Ctrl key and hit X. Type "Y" to save the file and exit.

The grep command I gave was for illustration.  The regular expression "^\#" represents lines that begin with the hash mark.  The carat ("^") represents the start of the line, and I used "\#" to "escape" the hash mark so the bash shell would not try to interpret it as the beginning of a comment.  Using "grep -v" returns only lines that don't match the pattern, so the command I used prints just the lines that do not start with a hash mark.

You could, if you prefer, enter all the lines in the standard file including the comments.  If you want to do that, just use all the text in the first block of code I posted above.

---

### Post by Veronica_Sanford on 2016-03-02
Thanks to both of you! I believe I figured it out, although the file has a different name now: dhclient.conf.save . Is that going to be an issue anywhere?

---

### Post by Hadaka on 2016-03-02
Yes the file name does make a difference..dhclient.conf.save needs to be renamed.
please open a terminal...ctrl/alt/t...then copy and paste..one line at a time..please do..
```
cp dhclient.conf.save dhclient.conf
sudo cp dhclient.conf /etc/dhcp
```
then do..
```
cd /etc/dhcp
cat dhclient.conf
```
to verify it copied over correctly
thanks.

---

