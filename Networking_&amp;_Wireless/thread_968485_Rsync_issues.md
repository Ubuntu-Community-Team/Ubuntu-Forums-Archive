---
title: "Rsync issues"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by jbrown96 on 2008-11-02
I'm trying out rsync for the first time, and I really like it, but I'm having a couple of issues. They both have to do with syncing via SSH. 
First, how do I use non-standard ports? I have tried ```
rsync -avzre ssh -p 248 192.168.1.102:/home/justin/media/Videos/Family\ Guy/ /home/justin/media/Videos/

``` ```
rsync -avzre ssh --port=248 192.168.1.102:/home/justin/media/Videos/Family\ Guy/ /home/justin/media/Videos/

``` and I have also tried both versions with the port flag before ssh, but I always get the following error > Unexpected remote arg: 192.168.1.102:/home/justin/media/Music/
rsync error: syntax or usage error (code 1) at main.c(1220) [sender=3.0.3]


Second, how do I deal with file names with spaces. Even after I switched my server back to the default port, I cannot sync because of the space in "family guy". How would I type the file name? I thought the "\" was for filenames with spaces.

Thanks for the help

---

### Post by hackeron on 2008-11-22
Anyone? -- I'm having the same issue but not with spaces but '(' or ')' in filename.

---

### Post by ameno on 2008-12-16
to use options for ssh quote them. imho thats a bug in rsync.
e.g. -e /usr/bin/ssh -p 22 -i /root/.ssh/bla_dsa WONT work
but -e "/usr/bin/ssh -p 22 -i /root/.ssh/bla_dsa" DOES WORK

another way is to use the various ssh_config files (see man ssh_config).

rsync is really picky about cli arguments. thats why i have found this topic in the first place ;)
there is a bug in rsnapshot <1.3.1 that triggers the same thing. intrepid uses 1.3.0-2 :(

for the spaces... there is a special option to protect arguments (-s), see the manpage of rsync.
but escaping with \ should work too (as stated in the manpage)
you may wanna try with a combination of both plus " or ' in various places (around the dir only, around the whole remote arg etc) :)

---

### Post by joebeasley on 2008-12-17
The -p is for perms.  --port is not a valid option.  use host:port.

rsync -avzre ssh 192.168.1.102:248/home/justin/media/Videos/Family\ Guy/ /home/justin/media/Videos/


ssh is the default, so you could probably leave off the 'e' and 'ssh' options.

---

