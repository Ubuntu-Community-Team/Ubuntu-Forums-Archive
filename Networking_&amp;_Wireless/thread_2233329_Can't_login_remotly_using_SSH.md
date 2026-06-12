---
title: "Can't login remotly using SSH"
date: 2014-07-07
forum: Networking &amp; Wireless
---

### Post by simon45 on 2014-07-07
Hi everyone,
     I'm currently using Ubuntu Server 12.04 and I have an issue login in using SSH.

     When i try to login via SSH from another computer I always get an error (Connexion refused). When I try to log in with SSH from my server it works fine.

     I've also tried to ping my server from another computer (inside and outside of my network) and it works.

     I really don't know where to start to look at.

     Also it seems that Apache and my FTP server stopped at the same time. (I can't tell you if ti's related or not)

Any help on this would be very appreciated.
Thank you very much and have a nice day
--Simon

---

### Post by papibe on 2014-07-07
Hi simon45. Welcome to the forum ):P

Could you post the content of the log of a failed attempt using the triple verbose option?
```
ssh -vvv yourserver
```
Regards

---

### Post by Lars Noodén on 2014-07-08
> **simon45 said:**
>      Also it seems that Apache and my FTP server stopped at the same time. (I can't tell you if ti's related or not)

My guess would be that there is a problem with the firewall on the server.  Maybe somehow it got activated when it wasn't active before or else got reset to the default values.  

```

sudo ufw status verbose

```

---

### Post by simon45 on 2014-07-08
> **papibe said:**
> Hi simon45. Welcome to the forum ):P

Could you post the content of the log of a failed attempt using the triple verbose option?
```
ssh -vvv yourserver
```
Regards

Hi papibe,
Thank you for you real quick answer.

here's the result of the command you asked me to try

```
[FONT=arial]OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011[/FONT][FONT=arial]debug1: Reading configuration data /etc/ssh_config[/FONT]
[FONT=arial]debug1: /etc/ssh_config line 20: Applying options for *[/FONT]
[FONT=arial]debug2: ssh_connect: needpriv 0[/FONT]
[FONT=arial]debug1: Connecting to 192.168.1.100 [192.168.1.100] port 1022.[/FONT]
[FONT=arial]debug1: connect to address 192.168.1.100 port 1022: Connection refused[/FONT]
[FONT=arial]ssh: connect to host 192.168.1.100 port 1022: Connection refused[/FONT]
```

Thank you very much again and have a nice day
--Simon

---

### Post by bobnn on 2014-07-08
"debug1: connect to address 192.168.1.100 **port 1022**: Connection refused" 

port 1022 is not the standard - port 22 is - are you using the same port for all your test connections?

ETA: I'm thinking that  Lars Noodén's comment is also (more?) appropriate - a firewall change would account for all 3 issues.

---

### Post by papibe on 2014-07-08
Thanks.

As bobnn is pointing out, 1022 is not the default ssh port.

A couple of questions?
[LIST]
[*]Did you change the listening ssh port on the server?
[*]Did you run the ssh command with the '-p1022' option, or do you have a personal ~/.ssh/config file?
[/LIST]
Regards.

---

### Post by simon45 on 2014-07-08
> **papibe said:**
> Thanks.

As bobnn is pointing out, 1022 is not the default ssh port.

A couple of questions?
[LIST]
[*]Did you change the listening ssh port on the server?
[*]Did you run the ssh command with the '-p1022' option, or do you have a personal ~/.ssh/config file?
[/LIST]
Regards.

Hi,
     Thanks everyone for your help.

     I've changed the port to 1022 and yes I've run the command using the -p 1022 option.

     For the personnal ~/.ssh/config file I don't think I have any (where could I find this).

     I've also looked at my router and the 1022 port is properly forwarded to the my server.

I've also tried to run ssh from my server using my external ip address and it works fine

```
ssh 123.456.789.111
``` I didn't specify the port and it worked

Thank you very much for your help
--Simon

---

### Post by simon45 on 2014-07-11
Does anyone have any other ideas ?

Thank you very much and have a nice day
--Simon

---

### Post by steeldriver on 2014-07-11
Where are you trying to connect from - inside the same LAN as the target machine? or from somewhere else, such as a computer at work?. Are you using the target machine's hostname? or the LAN IP? or a public IP? Please give as much detail as you can about your setup and the exact commands that you're using.

---

### Post by simon45 on 2014-07-11
Hi Steeldriver,
     I try to connect from a computer un the same LAN. I've tryed with both the LAN server IP address and the public IP address

     The command that I use is

```
ssh 192.168.1.100 -p 1022
```

Thank you very much for you quick answer.
--Simon

---

### Post by steeldriver on 2014-07-11
OK thanks - and can you post the output of

```

sudo netstat -nltp | grep :1022

sudo lsof -i :1022

```

---

### Post by simon45 on 2014-07-11
> **steeldriver said:**
> OK thanks - and can you post the output of

```

sudo netstat -nltp | grep :1022

sudo lsof -i :1022

```

```

sudo netstat -nltp | grep :1022

```
[TABLE="width: 500, align: center"]
[TR]
[TD]tcp[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0.0.0.0:1022[/TD]
[TD]0.0.0.0:*[/TD]
[TD]LISTEN[/TD]
[TD]581/sshd[/TD]
[/TR]
[TR]
[TD]tcp6[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]:::1022[/TD]
[TD]:::*[/TD]
[TD]LISTEN[/TD]
[TD]581/sshd[/TD]
[/TR]
[/TABLE]

```

sudo lsof -i :1022

```
[TABLE="width: 500, align: center"]
[TR]
[TD]sshd[/TD]
[TD]581[/TD]
[TD]root[/TD]
[TD]3u[/TD]
[TD]IPv4[/TD]
[TD]8267[/TD]
[TD]0t0[/TD]
[TD]TCP[/TD]
[TD]*:1022 (LISTEN)[/TD]
[/TR]
[TR]
[TD]sshd[/TD]
[TD]581[/TD]
[TD]root[/TD]
[TD]4u[/TD]
[TD]IPv6[/TD]
[TD]8269[/TD]
[TD]0t0[/TD]
[TD]TCP[/TD]
[TD]*:1022 (LISTEN)[/TD]
[/TR]
[/TABLE]


sshd    581    root    3u    IPV4    8267    0t0    TCP    *:1022    (LISTEN)
sshd    581    root    4u    IPV6    8269    0t0    TCP    *:1022    (LISTEN)

Thank you very much and have a nice day
--Simon

---

### Post by Lars Noodén on 2014-07-12
What about the firewall settings as per #3 above?  Is port 1022 opened for incoming TCP?

---

### Post by simon45 on 2014-07-12
I only have a routeur (no firewall software, or dedicated firewall) and the 1022 port is forwarded to my server internal IP

Thank you very much
--Simon

---

### Post by Lars Noodén on 2014-07-13
The Ubuntu machine you are trying to connect to has a built in firewall (packet filter) called iptables.  It can be accessed directly or via the UFW interface.  The default is that it (UFW) lets everything through.  However, if it gets turned on, then the default on settings are to block just about everything.  The symptoms would be as you describe, so it is worth checking to be sure.  

```

sudo ufw status verbose

```

If it is turned off, then we can look elsewhere.  If it is turned on, then port 1022 needs to be opened.

---

### Post by simon45 on 2014-07-13
> **Lars Noodén said:**
> The Ubuntu machine you are trying to connect to has a built in firewall (packet filter) called iptables.  It can be accessed directly or via the UFW interface.  The default is that it (UFW) lets everything through.  However, if it gets turned on, then the default on settings are to block just about everything.  The symptoms would be as you describe, so it is worth checking to be sure.  

```

sudo ufw status verbose

```

If it is turned off, then we can look elsewhere.  If it is turned on, then port 1022 needs to be opened.

I ran this command and it says that it's disable.

Thank you very much and have a nice day
--Simon

---

### Post by steeldriver on 2014-07-13
Can you confirm that you ran the netstat and lsof commands on the target server (not on the client from which you are trying to connect)? Despite the lsof and netstat results you posted, it really does seem like there is no ssh server listening on port 1022 (especially since you mentioned that when you successfully connected from the same server, you did not specify a non-standard port - suggesting that if there *is* an sshd process running, it is listening on :22)

---

### Post by simon45 on 2014-07-13
> **steeldriver said:**
> Can you confirm that you ran the netstat and lsof commands on the target server (not on the client from which you are trying to connect)? Despite the lsof and netstat results you posted, it really does seem like there is no ssh server listening on port 1022 (especially since you mentioned that when you successfully connected from the same server, you did not specify a non-standard port - suggesting that if there *is* an sshd process running, it is listening on :22)
I've ran both command on the target server with the following result:

```

sudo netstat -nltp | grep :1022

```
[TABLE="width: 500, align: center"]
[TR]
[TD]tcp[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0.0.0.0:1022[/TD]
[TD]0.0.0.0:*[/TD]
[TD]LISTEN[/TD]
[TD]581/sshd[/TD]
[/TR]
[TR]
[TD]tcp6[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]:::1022[/TD]
[TD]:::*[/TD]
[TD]LISTEN[/TD]
[TD]581/sshd[/TD]
[/TR]
[/TABLE]

```

sudo lsof -i :1022

```
[TABLE="width: 500, align: center"]
[TR]
[TD]sshd[/TD]
[TD]581[/TD]
[TD]root[/TD]
[TD]3u[/TD]
[TD]IPv4[/TD]
[TD]8267[/TD]
[TD]0t0[/TD]
[TD]TCP[/TD]
[TD]*:1022 (LISTEN)[/TD]
[/TR]
[TR]
[TD]sshd[/TD]
[TD]581[/TD]
[TD]root[/TD]
[TD]4u[/TD]
[TD]IPv6[/TD]
[TD]8269[/TD]
[TD]0t0[/TD]
[TD]TCP[/TD]
[TD]*:1022 (LISTEN)[/TD]
[/TR]
[/TABLE]

Thank you very much and have a nice day
--Simon

---

### Post by ubudog on 2014-07-13
Hi,

Can you post the output of:
```
sudo cat /etc/ssh/sshd_config | grep Port
```
on your server, just to be sure?

---

### Post by simon45 on 2014-07-13
> **ubudog said:**
> Hi,

Can you post the output of:
```
sudo cat /etc/ssh/sshd_config | grep Port
```
on your server, just to be sure?

```
Port 1022
```

Thank you very much and have a nice day
--Simon

---

### Post by simon45 on 2014-07-15
I've made another test.

When I just boot boot up my server I can access it using SSH from another computer for about 1 or 2 minutes and then it kicks me out. Once I'm kicked out, I cannot access it again.

Thank you very much for your help.
--Simon

---

