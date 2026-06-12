---
title: "Virtual Hosts of Apache2 are not working =("
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by Pegasus_from_UA on 2007-12-27
HI all
First of all sorry for my poor English please... 
I instaled Apache2
made Virtual Host like this [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)
and saw 
```
[warn] NameVirtualHost *:0 has no VirtualHosts
```
but 2 virtual hosts worked.
then all were broken. I don't know why...
Then I commeted out

```
#Include /etc/apache2/mods-enabled/*.load
#Include /etc/apache2/mods-enabled/*.conf
```

And I included next file /etc/apache2/extra/loadmodules.conf

```
#modules
Include /etc/apache2/extra/loadmodules.conf
```[/CODE]

```
 cat /etc/apache2/extra/loadmodules.conf
LoadModule authn_file_module /usr/lib/apache2/modules/mod_authn_file.so
LoadModule authn_dbm_module /usr/lib/apache2/modules/mod_authn_dbm.so
LoadModule authn_anon_module /usr/lib/apache2/modules/mod_authn_anon.so
LoadModule authn_dbd_module /usr/lib/apache2/modules/mod_authn_dbd.so
LoadModule authn_default_module /usr/lib/apache2/modules/mod_authn_default.so
LoadModule authn_alias_module /usr/lib/apache2/modules/mod_authn_alias.so
LoadModule authz_host_module /usr/lib/apache2/modules/mod_authz_host.so
LoadModule authz_groupfile_module /usr/lib/apache2/modules/mod_authz_groupfile.so
LoadModule authz_user_module /usr/lib/apache2/modules/mod_authz_user.so
LoadModule authz_dbm_module /usr/lib/apache2/modules/mod_authz_dbm.so
LoadModule authz_owner_module /usr/lib/apache2/modules/mod_authz_owner.so
LoadModule authnz_ldap_module /usr/lib/apache2/modules/mod_authnz_ldap.so
LoadModule authz_default_module /usr/lib/apache2/modules/mod_authz_default.so
LoadModule auth_basic_module /usr/lib/apache2/modules/mod_auth_basic.so
LoadModule auth_digest_module /usr/lib/apache2/modules/mod_auth_digest.so
LoadModule file_cache_module /usr/lib/apache2/modules/mod_file_cache.so
LoadModule cache_module /usr/lib/apache2/modules/mod_cache.so
LoadModule disk_cache_module /usr/lib/apache2/modules/mod_disk_cache.so
LoadModule mem_cache_module /usr/lib/apache2/modules/mod_mem_cache.so
LoadModule dbd_module /usr/lib/apache2/modules/mod_dbd.so
LoadModule dumpio_module /usr/lib/apache2/modules/mod_dumpio.so
LoadModule ext_filter_module /usr/lib/apache2/modules/mod_ext_filter.so
LoadModule include_module /usr/lib/apache2/modules/mod_include.so
LoadModule filter_module /usr/lib/apache2/modules/mod_filter.so
LoadModule charset_lite_module /usr/lib/apache2/modules/mod_charset_lite.so
LoadModule deflate_module /usr/lib/apache2/modules/mod_deflate.so
LoadModule ldap_module /usr/lib/apache2/modules/mod_ldap.so
LoadModule log_forensic_module /usr/lib/apache2/modules/mod_log_forensic.so
LoadModule env_module /usr/lib/apache2/modules/mod_env.so
LoadModule mime_magic_module /usr/lib/apache2/modules/mod_mime_magic.so
LoadModule cern_meta_module /usr/lib/apache2/modules/mod_cern_meta.so
LoadModule expires_module /usr/lib/apache2/modules/mod_expires.so
LoadModule headers_module /usr/lib/apache2/modules/mod_headers.so
LoadModule ident_module /usr/lib/apache2/modules/mod_ident.so
LoadModule usertrack_module /usr/lib/apache2/modules/mod_usertrack.so
LoadModule unique_id_module /usr/lib/apache2/modules/mod_unique_id.so
LoadModule setenvif_module /usr/lib/apache2/modules/mod_setenvif.so
LoadModule version_module /usr/lib/apache2/modules/mod_version.so
LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_connect_module /usr/lib/apache2/modules/mod_proxy_connect.so
LoadModule proxy_ftp_module /usr/lib/apache2/modules/mod_proxy_ftp.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule proxy_ajp_module /usr/lib/apache2/modules/mod_proxy_ajp.so
LoadModule proxy_balancer_module /usr/lib/apache2/modules/mod_proxy_balancer.so
LoadModule ssl_module /usr/lib/apache2/modules/mod_ssl.so
LoadModule mime_module /usr/lib/apache2/modules/mod_mime.so
LoadModule dav_module /usr/lib/apache2/modules/mod_dav.so
LoadModule status_module /usr/lib/apache2/modules/mod_status.so
LoadModule autoindex_module /usr/lib/apache2/modules/mod_autoindex.so
LoadModule asis_module /usr/lib/apache2/modules/mod_asis.so
LoadModule info_module /usr/lib/apache2/modules/mod_info.so
LoadModule suexec_module /usr/lib/apache2/modules/mod_suexec.so
LoadModule cgid_module /usr/lib/apache2/modules/mod_cgid.so
LoadModule cgi_module /usr/lib/apache2/modules/mod_cgi.so
LoadModule dav_fs_module /usr/lib/apache2/modules/mod_dav_fs.so
LoadModule dav_lock_module /usr/lib/apache2/modules/mod_dav_lock.so
LoadModule vhost_alias_module /usr/lib/apache2/modules/mod_vhost_alias.so
LoadModule negotiation_module /usr/lib/apache2/modules/mod_negotiation.so
LoadModule dir_module /usr/lib/apache2/modules/mod_dir.so
LoadModule imagemap_module /usr/lib/apache2/modules/mod_imagemap.so
LoadModule actions_module /usr/lib/apache2/modules/mod_actions.so
LoadModule speling_module /usr/lib/apache2/modules/mod_speling.so
LoadModule userdir_module /usr/lib/apache2/modules/mod_userdir.so
LoadModule alias_module /usr/lib/apache2/modules/mod_alias.so
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
```

Now I haven't message like 
```
[warn] NameVirtualHost *:0 has no VirtualHosts
```
I have next  
```
$ /usr/sbin/apache2 -S
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:*                    is a NameVirtualHost
         default server www.buznet.group (/etc/apache2/sites-enabled/www.buznet.group:6)
         port * namevhost www.buznet.group (/etc/apache2/sites-enabled/www.buznet.group:6)
         port * namevhost www.phpmyadmin.group (/etc/apache2/sites-enabled/www.phpmyadmin.group:5)
         port * namevhost www.sams.group (/etc/apache2/sites-enabled/www.sams.group:5)
Syntax OK
```
but VirtualHosts are  not working ....
Why ? 
Please Help :shock::shock::shock:

---

### Post by Pegasus_from_UA on 2007-12-27
too bad... =(

---

### Post by freymann on 2007-12-27
In the documentation I read when first setting things up, I was told to simply copy the existing file to my new virtual host. Which I did.

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite
```

I edited the DocumentRoot, Directory, and whatever else I needed and saved this.

Then I made my site active

```
sudo a2ensite mysite
```

and restarted apache

```
sudo /etc/init.d/apache2 restart
```

and I received the error messages about no virtual hosts.

I think the solution was to simply edit the file I copied and delete the line

```
NameVirtualHost *
```

from my "copy" of the original I used to create my virtual host.

In my case, I have two virtual sites runnings. I just edited the default for the first, copied it over to the second virtual host, edited. 

I went back to the copied and edited file and removed the NameVirtualHost line from it, so it only appears ONCE in all the virtual host stuff.

My error went away after that I believe.

---

### Post by Pegasus_from_UA on 2007-12-27
**freymann**
thanks for answer ;)
I tried to do like you done 
but It didn't working
now I just written in /etc/hosts
```
169.254.10.13   www.sams.group sams.group www.buznet.group buznet.group
192.168.0.1      www.sams.group sams.group www.buznet.group buznet.group
```
and now it's working 
strange 
I commented out in /etc/apache2/apache2.conf
```
#Include /etc/apache2/extra/httpd-vhosts.conf
```
```
~# cat /etc/apache2/extra/httpd-vhosts.conf
#
#  We're running multiple virtual hosts.
#
NameVirtualHost *
```
and added below
```
NameVirtualHost *
```
but "NameVirtualHost *" and "/etc/apache2/extra/httpd-vhosts.conf" it is the same thing!
:confused:

---

### Post by Pegasus_from_UA on 2007-12-27
my fault next
Virtual Host didn't  work in local computer couse  I written 
```
Include /etc/apache2/extra/httpd-vhosts.conf
```
at /etc/apache2/apache2.conf twice
and now when I fixed this virtual hosts are working in local computer 
and now I need to install DNS server for virtual hosts can work with other computers from LAN

---

