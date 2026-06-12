---
title: "access to samba share fails"
date: 2019-04-04
forum: Networking &amp; Wireless
---

### Post by mpbwebdev on 2019-04-04
Hi Guys,

I have an Ubuntu Server setup for file share. I administrator the server mostly via Webmin.
I have multiple users accessing the shared folders, each having a secure username and password.

All accounts and folder share permissions are configured correctly as I can access all as intended.
All users have win10, win8 and win7 pc's with the same antivirus installed and configured.

I have 1 pc refusing to connect to the ubuntu server with "Username and password incorrect"
Regardless of the username and password I use, always the same error occur.
These credentials work just fine from any other pc.

i also enabled the smb1 features.

Below is the last few lines in the samba log file for this user 

[2019/04/04 13:35:01.096621,  3] ../source3/param/loadparm.c:1609(lp_add_ipc)
  adding IPC service
[2019/04/04 13:35:01.096645,  3] ../source3/auth/auth.c:189(auth_check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [Jacqueline-PC]\[Jacqueline]@[JACQUELINE-PC] with the new password interface
[2019/04/04 13:35:01.096661,  3] ../source3/auth/auth.c:192(auth_check_ntlm_password)
  check_ntlm_password:  mapped user is: [Jacqueline-PC]\[Jacqueline]@[JACQUELINE-PC]
[2019/04/04 13:35:01.097829,  3] ../source3/passdb/lookup_sid.c:1680(get_primary_group_sid)
  Forcing Primary Group to 'Domain Users' for Jacqueline
[2019/04/04 13:35:01.097912,  2] ../libcli/auth/ntlm_check.c:430(ntlm_password_check)
  ntlm_password_check: NTLMv1 passwords NOT PERMITTED for user Jacqueline
[2019/04/04 13:35:01.097928,  3] ../libcli/auth/ntlm_check.c:437(ntlm_password_check)
  ntlm_password_check: NEITHER LanMan nor NT password supplied for user Jacqueline
[2019/04/04 13:35:01.098107,  2] ../source3/auth/auth.c:332(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [Jacqueline] -> [Jacqueline] FAILED with error NT_STATUS_WRONG_PASSWORD, authoritative=1
[2019/04/04 13:35:01.098152,  2] ../auth/auth_log.c:760(log_authentication_event_human_readable)
  Auth: [SMB2,(null)] user [Jacqueline-PC]\[Jacqueline] at [Thu, 04 Apr 2019 13:35:01.098140 SAST] with [NTLMv1] status [NT_STATUS_WRONG_PASSWORD] workstation [JACQUELINE-PC] remote host [ipv4:192.168.50.199:64762] mapped to [Jacqueline-PC]\[Jacqueline]. local host [ipv4:192.168.50.109:445] 
[2019/04/04 13:35:01.098244,  2] ../auth/auth_log.c:220(log_json)
  JSON Authentication: {"timestamp": "2019-04-04T13:35:01.098190+0200", "type": "Authentication", "Authentication": {"version": {"major": 1, "minor": 0}, "status": "NT_STATUS_WRONG_PASSWORD", "localAddress": "ipv4:192.168.50.109:445", "remoteAddress": "ipv4:192.168.50.199:64762", "serviceDescription": "SMB2", "authDescription": null, "clientDomain": "Jacqueline-PC", "clientAccount": "Jacqueline", "workstation": "JACQUELINE-PC", "becameAccount": null, "becameDomain": null, "becameSid": "(NULL SID)", "mappedAccount": "Jacqueline", "mappedDomain": "Jacqueline-PC", "netlogonComputer": null, "netlogonTrustAccount": null, "netlogonNegotiateFlags": "0x00000000", "netlogonSecureChannelType": 0, "netlogonTrustAccountSid": "(NULL SID)", "passwordType": "NTLMv1"}}
[2019/04/04 13:35:01.098273,  2] ../auth/gensec/spnego.c:605(gensec_spnego_server_negTokenTarg)
  SPNEGO login failed: NT_STATUS_WRONG_PASSWORD
[2019/04/04 13:35:01.098334,  3] ../source3/smbd/smb2_server.c:3139(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_LOGON_FAILURE] || at ../source3/smbd/smb2_sesssetup.c:134
[2019/04/04 13:35:01.098999,  3] ../source3/smbd/server_exit.c:244(exit_server_common)
  Server exit (NT_STATUS_CONNECTION_RESET)

I hope you can assist with this endless error I'm experiencing.

---

### Post by Morbius1 on 2019-04-04
From the log the credentials you are passing for this share are incorrect. At least they are incorrect for the "unmapped" "Forcing Primary Group to 'Domain Users for Jacqueline" user. And it seems you are accessing it with an old security protocol ( ntlm_password_check: NTLMv1 passwords NOT PERMITTED for user Jacqueline ).

You might want to post the output of the following command so that folks  here can see that you are using winbind and other things on your samba  server:
```
testparm -s
```
Anyway, those familiar with setting up a Domain Server will need to see how samba is set up.

---

### Post by mpbwebdev on 2019-04-05
Here is the result from testparm -s


Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Erika]"
Processing section "[Ashton]"
Processing section "[Diane]"
Processing section "[Elsabe]"
Processing section "[Gavin]"
Processing section "[Gert]"
Processing section "[Gillian]"
Processing section "[Kathy]"
Processing section "[Matthew]"
Processing section "[Melanie]"
Processing section "[Nateshia]"
Processing section "[Steve]"
Processing section "[monrico]"
Processing section "[Fingroup_Backups]"
Processing section "[Ruzel]"
Processing section "[Email_Backups]"
Processing section "[Fileserver_Backups]"
Processing section "[Test]"
Processing section "[Jacqueline]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE


# Global parameters
[global]
        dns proxy = No
        log file = /var/log/samba/log.%m
        map to guest = Bad User
        max log size = 1000
        obey pam restrictions = Yes
        pam password change = Yes
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        read raw = No
        server role = standalone server
        server string = %h server (Samba, Ubuntu)
        syslog = 0
        unix password sync = Yes
        usershare allow guests = Yes
        winbind trusted domains only = Yes
        winbind use default domain = Yes
        wins support = Yes
        write raw = No
        idmap config * : backend = tdb




[printers]
        browseable = No
        comment = All Printers
        create mask = 0700
        path = /var/spool/samba
        printable = Yes




[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers




[Erika]
        path = /media/Email_Backups/Erika
        valid users = Erika finadmin
        write list = Erika finadmin




[Ashton]
        path = /media/Email_Backups/Ashton
        valid users = Ashton finadmin
        write list = Ashton finadmin




[Diane]
        path = /media/Email_Backups/Diane
        valid users = Diane finadmin
        write list = Diane finadmin




[Elsabe]
        path = /media/Email_Backups/Elsabe
        valid users = Elsabe finadmin
        write list = Elsabe finadmin




[Gavin]
        path = /media/Email_Backups/Gavin
        valid users = Gavin finadmin
        write list = Gavin finadmin




[Gert]
        path = /media/Email_Backups/Gert
        valid users = Gert finadmin
        write list = Gert finadmin




[Gillian]
        path = /media/Email_Backups/Gillian
        valid users = Gillian finadmin
        write list = Gillian finadmin




[Kathy]
        path = /media/Email_Backups/Kathy
        valid users = Kathy finadmin
        write list = Kathy finadmin




[Matthew]
        path = /media/Email_Backups/Matthew
        valid users = Matthew finadmin
        write list = Matthew finadmin




[Melanie]
        path = /media/Email_Backups/Melanie
        valid users = Melanie finadmin
        write list = Melanie finadmin




[Nateshia]
        path = /media/Email_Backups/Nateshia
        valid users = Nateshia finadmin
        write list = Nateshia finadmin




[Steve]
        create mask = 0777
        directory mask = 0777
        path = /media/Email_Backups/Steve
        valid users = Steve finadmin
        write list = Steve finamin




[monrico]
        path = /media/Email_Backups/monrico
        valid users = monrico finadmin
        write list = monrico finadmin




[Fingroup_Backups]
        create mask = 0777
        directory mask = 0777
        path = /media/Fingroup_Backups
        valid users = finadmin
        write list = finadmin




[Ruzel]
        path = /media/Email_Backups/Ruzel
        valid users = Ruzel finadmin
        write list = Ruzel finadmin




[Email_Backups]
        path = /media/Email_Backups
        valid users = finadmin
        write list = finadmin




[Fileserver_Backups]
        path = /media/Fileserver_Backups
        valid users = finadmin
        write list = finadmin




[Test]
        create mask = 0777
        directory mask = 0777
        path = /mnt/Test
        valid users = @users
        write list = @users




[Jacqueline]
        path = /media/Email_Backups/Jacqueline
        valid users = Jacqueline
        write list = Jacqueline

---

