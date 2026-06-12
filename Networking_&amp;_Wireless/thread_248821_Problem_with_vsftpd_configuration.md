---
title: "Problem with vsftpd configuration"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by tarun86 on 2006-09-01
I am tryin to set a vsftd server on my machine. Right now for testing purpose I am allowing anon users but thats not the problem.
Problem is that I think I have configured the /etc/vsftpd.conf file properly and when i do /etc/init.d/vsftpd start it says:
[I]root@Mysterio:/etc# /etc/init.d/vsftpd start
 * Starting FTP server: vsftpd                                                                                                                       [ ok ][/I]

which means the server has started. Now when I do /etc/init.d/vsftpd stop it says :
[B]root@Mysterio:/etc# /etc/init.d/vsftpd stop
 * Stopping FTP server: vsftpd                                                                                                                              No /usr/sbin/vsftpd found running; none killed.
                                                                                                                                                     [ ok ]
[/B]
And I am out of what is happening here ??? and I am not able to connect to the ftp server that has started but is invisble
Any sort of help is welcomed . If i m doing anything wrong let me know 

My /etc/vsftpd.conf 
======================================
listen=YES
background=YES
# listen_address=
anonymous_enable=YES
ftp_username=tarun
anon_root=/home/MyDownloads/
local_umask=022
#[$ftp_username's home directory]
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_world_readable_only=NO
anon_max_rate=0
idle_session_timeout=300
ascii_download_enable=NO
ascii_upload_enable=NO
connect_from_port_20=NO
port_enable=YES
hide_ids=NO
log_ftp_protocol=NO
syslog_enable=NO
max_per_ip=0
# cmds_allowed=
local_root=/usr/share/empty
nopriv_user=nobody
ftpd_banner=(vsFTPd 1.2.0)
======================================
and I am dapper .Please help me ... any sample working file or any suggestion or correction will be appreciated 
thanks

---

