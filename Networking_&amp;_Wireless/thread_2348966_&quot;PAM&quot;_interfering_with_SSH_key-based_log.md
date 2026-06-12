---
title: "&quot;PAM&quot; interfering with SSH key-based login configuration"
date: 2017-01-09
forum: Networking &amp; Wireless
---

### Post by spacer.x-infinity on 2017-01-09
Hello,
Extreme newbie here. Please tailor your responses accordingly. :)

My basic situation is this:

I am trying to get two hard-install Kubuntu  14.04 laptops to talk to each other over SSH via a home wifi network  that is shared with one other desktop computer that does not belong to  me and that I don't want included in my SSH server. At least to start  with, I would like to have standard key-based authentication set up  between these two laptops, but my ultimate hope is to set up a static  key VPN between them and maybe even upgrade to some form of 2-factor  authentication at a later date. But, until I feel a little more proficient with Linux in  general, I just want to keep things as simple as possible... which  brings me to my problem.

Several months ago, I did successfully manage to set up key-based login  between a hard-install Kubuntu 14.04 laptop and what was then a Kubuntu  14.04 VM running on a Windows 7 host. It worked fine for a while but  then, without sufficient knowledge of what I was doing, I tried setting  up the aforementioned static key VPN. I'm not exactly sure what I did  wrong but I think that, while I was configuring iptables to run the VPN,  some rule or combination of rules that I put in place completely  knocked out the bridged network connection between my VM and my host  OS. 

Flash forward to today: I've abandoned the whole idea of keeping a VM on  one laptop and opted for a hard install on both of them. When I first  managed to transfer the public key from the hard-install machine over to  the VM, I seem to recall that the *ssh-copy-id*  command didn't work for me because it wouldn't let me specify the  directory in which to put it. In stead, I had to use 

```
cat ~/.ssh/id_rsa.pub | ssh <YourIP> "mkdir -p ~/.ssh  && >> ~/.ssh/authorized_keys"
``` 

This worked fine when I attempted it several months ago but no such  luck this time around. To run the above command, you obviously need to  have basic password authentication functioning properly, which I  currently don't. I just get *Permission denied, please try  again*. At first, I wasn't entirely sure why but then I  started looking at various tutorials online and stumbled on one that  suggested looking at */var/log/auth.log* to see if I  could get a clearer idea of what was going on. When I opened *auth.log* in my text editor, there were a few entries that particularly caught my attention:

```

Jan  7 17:40:53 aux-user-305V4A-305V5A-3415VA sshd[2836]: Invalid user primary-user from 192.168.x.xxx
Jan  7 17:40:53 aux-user-305V4A-305V5A-3415VA sshd[2836]: input_userauth_request: invalid user primary-user [preauth]
Jan  7 17:41:04 aux-user-305V4A-305V5A-3415VA sshd[2836]: pam_unix(sshd:auth): check pass; user unknown
Jan  7 17:41:04 aux-user-305V4A-305V5A-3415VA sshd[2836]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.108 
Jan  7 17:41:06 aux-user-305V4A-305V5A-3415VA sshd[2836]: Failed password for invalid user primary-user from 192.168.x.xxx port 49234 ssh2

```

Having never heard of this "pam" thing before, I didn't quite know what to make of it. My first thought was "I hope it isn't some automated script trying to brute-force my machine." I never even encountered it back when I managed to successfully configure SSH keys on my old VM. Upon looking closer at my *sshd_config* file, I read the following:

```

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

```

Not until I did a little more reading online did I come to find out that PAM is an alternate authentication method that the standard key-based configuration must be able to bypass in order to work properly. However, in order to properly configure SSH keys, I need to enable PasswordAuthentication so that I can transfer the public key from the server machine over to the client machine - which is precisely what the above stanza, assuming I understand it correctly, says I *can't* do if I want to bypass PAM effectively. 

So where exactly does this leave me? Ideally, I'd rather just have nothing whatsoever to do with PAM until I have a better handle on the basics of SSH and key-based authentication. Even if this means reverting to an older version of the SSH package that doesn't use PAM at all, I'd be willing to do that. Is this even possible or is there some other way to bypass PAM and implement SSH keys? If so, what is it and, if not, will I be forced to learn the inner workings of PAM before I can have a functioning SSH connection? Also, why does it say in the log file quoted above that my server machine was trying to connect to the client via port 49234 on ssh2 when the *sshd_config* file on both machines says its connecting via port 22? Could this also be part of the problem and, if so, how can I rectify it?

Thanks in advance for any help you can provide. 

Cheers. :)

---

### Post by TheFu on 2017-01-10
TL;DR.  Don't know what a "hard install" means.

Getting ssh key-based authentication working isn't hard.
[LIST=1]
[*]Setup static IPs for all ssh-server systems.
[*]Get system-names known to all systems. Either edit the /etc/hosts or setup DHCP reservations inside your router or DHCP server.
[*]**ping** a-server  # must work by name, not IP. Well, that isn't entirely true, but .... 
[*]ping b-server  # must work by name, not IP.
[*]**ssh-keygen** on both machines to create ssh-key pairs (private and public)
[*]**ssh-copy-id** from each machine to the other, to swap public keys. Stay with the defaults
[*]No need to touch PAM settings. The default settings do not impact ssh for passwords or keys.
[*]Manually copying keys means you have to be extremely careful about ~/.ssh/ and permissions for files inside that directory. ssh-copy-id does the right thing.
[/LIST]

So, if you didn't touch any files in /etc/PAM* - then you haven't done anything bad.

To start over, just **rm -rf ~/.ssh** on each machine. No sudo needed.

ssh troubleshooting. [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)
ssh security. [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

I like ssh.

---

### Post by spacer.x-infinity on 2017-01-11
Yeah, SSH seems pretty cool. I just feel as though I've barely scratched the surface of what I'm able to do with it. :-k

By "hard install," I just meant that it's the only operating system on either of my machines, as opposed to a VM or disk partition. Maybe I just don't quite have the "lingo" down yet.

Anyway, thanks a lot for your help. I'll give your suggestions a try when I have a little more time and see how it goes.

---

### Post by TheFu on 2017-01-12
That is just a normal install, only OS on the system. No need to mention it in most cases.  It is worth mentioning dual-boot or VM installs for things regarding firewall issues or booting issues.  I hope you used a few disk partitions for the install. That is the normal method.

There are so many things that cause issues because people don't setup normal, expected, static networking between their different systems. Unix uses IP and it expects this. It is a standard.  If you run avahi, then machines can find each other using {hostname}.local naming.  I find that tiresome and find editing /etc/hosts much easier.  I actually use a tool to manage the /etc/hosts files on all my systems (had about 30 at one point, down to about 20 now) easiest. Ansible (via ssh) is used to push any changes to that file out to all the systems.  ssh is the center of my use and management for all these systems.

---

