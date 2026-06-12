---
title: "Issue filesharing to Windows machine with Nautilus - Guest login"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by BartInTN on 2008-01-16
I'm having an issue when trying to fileshare from Ubuntu to a Windows machine (or another samba server, for that matter).  I want to explicitly describe what I've discovered to better help the next newbie who stumbles across this post.

From the Ubuntu dropdown menu, I select Places --> Network.  This opens Nautilus, showing me several network options including Windows Network.  I select Windows Network and am displayed a list of Windows domains/workgroups.  I select my workgroup, and my Windows/samba hosts are displayed.  So far, so good.

When connecting to a Windows/samba share where there is not guest account enabled (on the server side), Nautilus (on the client side) prompts me for a username and password.  Entering the correct credentials allows me to view the shares, transfer files, etc.  Exactly what I want.

But when connecting to a Windows/samba share where there is a guest account enabled, Nautilus uses the guest account by default.  I'm never prompted to enter credentials, nor is there any way for me to manually force Nautilus to use another set of credentials besides guest... at least using Nautlius to browse the network.  For my Windows machines, this is not a problem - I have the guest accounts disabled.  But I have a Linksys NAS200 device, which serves as a samba server.  The guest account is a permanent account in the NAS200, so it cannot be turned off.  So Nautlius connects to the NAS200 with the guest account then displays no shared folders, since I have denied the guest account access to them.  I discovered this using the smbclient command: 

me@mymachine:~$ smbclient -N -L 10.1.1.100
Anonymous login successful
Domain=[MYDOMAIN] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          IPC       IPC Service ()
        IPC$            IPC       IPC Service ()
Anonymous login successful

Which shows that anonymous (guest) login works, except that there are no shared folders for it to access.  Using smbclient with other credentials specified shows all the shared folders on the NAS200.

A workaround is to select the Connect to Server option in Nautlius.  Using Connect to Server, this only worked when I used the IP address of the sharing host (not hostname) for the server address;  I entered username and put in the workgroup name in the domain box.  This creates a link on the desktop as well as in the Places drop down menu.  Not what I want, but at least it works.

Now here's where I could use some guru help.  I would rather specify the username to use for a given Windows/samba server, as in the 'net use' command in Windows.  I would like it to be presistent, or something that could be scripted and run each boot time.  The trick that I can't seem to overcome is to have it specified system-wide, so that Nautilus uses it.  Then I could just browse the network in Nautilus and have it prompt me for the password for the correct set of credentials.

---

