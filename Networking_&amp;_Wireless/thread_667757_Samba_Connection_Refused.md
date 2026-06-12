---
title: "Samba Connection Refused"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by xhero0 on 2008-01-14
I am using 7.10, ubuntu. I am on mainly a win xp type network.... every time I try to see a share folder I get a connection refused. here is a log from xfssamba:

error connecting to 72.51.47.244 (connection refused)
Connection to MUSIC failed (Error NT_STATUS_CONNECTION_REFUSED)

Now whats weird is the ip of the machine is 192.168.105.21 and I have the exact same error trying to connect to other machines on the network.

I have tried a statically assign my nic
I cant 'browse' to the machine using PLACES/NETWORK

I can get on the internet...

any ideas???

joe m

---

### Post by evanchu on 2008-01-15
Let us collect some basic samba diagnostic information.  Download the script, samba-net-diag1, from [my page]("http://www.evanchu.com/linux2") in the "Basic Samba diagnostics" section.  Don't worry, it is a safe script.  You can read it.

Run it and post the output.  We can take a look at it.

---

### Post by xhero0 on 2008-01-15
Ok dumb question:

I forgot how to run a script, I saved it as a text type file without a extention....

I tried sudo sh sabma-net-diag1

thanx

---

### Post by dgray_from_dc on 2008-01-15
Are you sure that your smb.conf file is correct?  That's the first place you should look.  If your workgroups don't match, the machines won't be able to see each other easily.  There's a man page for it ```
man smb.conf
```
that is useful in showing you how (if that's the problem).

---

### Post by mimada on 2008-01-16
This problem seems to be happening a lot. Disable the iptables firewall and see if can access your shares. Install and use Firestarter if you plan to mess with the firewall. Firestarter is a gui front end for iptables. Hope this helps.

---

### Post by evanchu on 2008-01-16
> **xhero0 said:**
> 
I forgot how to run a script, I saved it as a text type file without a extention....
I tried sudo sh sabma-net-diag1


Save the script as whatever filename you like.  Then
```
bash samba-net-diag1
```
It will ask you the IP address of your Windows machine and its name.  Then it will print out a bunch of ouput.  Post the output.

I would not recommend doing
```
sudo sh anyscript
```
because you would be running the script as superuser.

---

### Post by xidahs on 2008-06-07
Had a similar problem with samba installed firestarter allowed connections from all computers on network in policy tab and allowed samba service but still no joy. Then I remembered to go to edit, preferences, advanced options and uncheck the Block broadcasts from external network and it was back again. Hope this helps

---

