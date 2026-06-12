---
title: "Samba: smbmount not working, smbclient is"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by kristianz on 2007-08-16
I have samba running nicely on my Ubuntu server, and it works perfectly with my Windows XP desktop computer. I now want to make the move to Ubuntu on my desktop computer as well, and experimented a bit with the Live CD. I had one problem: Mounting samba-shares from the Ubuntu server onto the Ubuntu Live desktop.

Strangely, browsing the share with smbclient works just fine (and remember, it works fine from XP as well), yet mounting the same share with smbmount fails. Here's what I do:

```
ubuntu@ubuntu:~$ smbmount  //paddy/samba mnt username=kvaks workgroup=WORKGROUP 
Password: 
10932: session setup failed: ERRDOS - ERRnoaccess (Access denied.) 
SMB connection failed 
ubuntu@ubuntu:~$
```
On the server this leaves the following in /var/log/syslog:

```
Aug 16 16:52:24 paddy nmbd[3981]: [2007/08/16 16:52:24, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
Aug 16 16:52:24 paddy nmbd[3981]:   find_domain_master_name_query_fail:
Aug 16 16:52:24 paddy nmbd[3981]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
```

This led me to put ```
domain master =  yes
``` in my smb.conf, but alas that did not seem to help the issue.

smbclient -L gives following output (and again, I am able to browse the shares with smbclient but not mount them):
```
ubuntu@ubuntu:~$ smbclient -U kvaks -L //paddy 
Password: 
Domain=[PADDY] OS=[Unix] Server=[Samba 3.0.24] 

       Sharename       Type      Comment 
       ---------       ----      ------- 
       IPC$            IPC       IPC Service () 
       samba           Disk 
       kvaks           Disk      Home directory of kvaks 
Domain=[PADDY] OS=[Unix] Server=[Samba 3.0.24] 

       Server               Comment 
       ---------            ------- 

       Workgroup            Master 
       ---------            ------- 
       WORKGROUP            PADDY 
ubuntu@ubuntu:~$
```

Incidently, I get the same error if I try to mount the samba share on the server itself.

I really need to samba to work on client-side before I make the move to Ubuntu for my desktop computer, since I have all my music stored on the server. I have googled the error-message from the log file, but could find no solution. I hope someone here can help me. I really want

---

### Post by misconfiguration on 2007-08-16
sudo mount -t smbfs //paddy/samba mnt username=kvaks /mount/point/to/local/box

also, on the client machine make sure you have samba and the samba front-end installed as well.

---

### Post by kristianz on 2007-08-16
smbmount and mount -f smbfs do the same thing, so naturally I get the same error. Surely I don't need a front-end to mount the share?

---

### Post by ktrnka on 2007-08-19
Have you installed smbfs?

---

### Post by dmizer on 2007-08-19
according to your first post, you're using this command for a mount:
```
smbmount  //paddy/samba [COLOR="Red"]mnt[/COLOR] username=kvaks workgroup=WORKGROUP
```

is that the exact line you used to mount the share?  i highlighted the problem part in red.  if this line is unedited, you will need to change that so it reads the complete path like so:
```
smbmount  //paddy/samba [COLOR="Red"]/mnt/mountpoint[/COLOR] username=kvaks workgroup=WORKGROUP
```
where "mountpoint" can be any directory _you create_ under /mnt

---

