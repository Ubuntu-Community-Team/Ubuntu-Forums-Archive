---
title: "Sharing /var/www with Samba Server"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Robe on 2006-11-01
Hi,

I've the Samba server working in Ubuntu Server and it's working ok. But I don't have any idea about how to share any directory.

Any body can tell me how to share the directory /var/www with full access.

Because I need to create a site and I want to work with Dreamweaver.

Thanks,

Robe.

---

### Post by Joe_CoT on 2006-11-01
There's a few steps for a setup like this, but it's overall a pretty painless process.

I assume you've already set up at least one samba user as describe [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service"),  or however method you chose to do it. I'll refer to it as <yoursambauser>

Firstly, we need a group allowed to read/write to /var/www
```

sudo addgroup www-users
sudo adduser <yoursambauser> www-users

```

now we give it write permissions to www
```

sudo chown -R root:www-users /var/www
sudo chmod -R 771 /var/www

```

Now edit your smb.conf
```
sudo nano -w /etc/samba/smb.conf
```

and add the following:

```

[www]
comment = www directory
path = /var/www
public = yes
writable = yes
valid users = <yoursambauser>
create mask = 0771
directory mask = 0771
force user = <yoursambauser>
force group = www-users

```

Now just restart samba and enjoy

```
sudo /etc/init.d/samba restart
```

---

