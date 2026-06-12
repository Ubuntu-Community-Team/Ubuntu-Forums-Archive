---
title: "Joining a windows network"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by PaddyIndigo on 2011-07-27
Hi
I'm having problems networking to my windows machine.  
I got the error "Unable to mount location" when I clicked on Network - Windows Network

I Googled and read a number of entries,  and as a result I changed the file smb.conf in /etc/samba/ and in /usr/share/samba to the workgroup name that my windows machine uses.  As a result I can "see" the workgroup when I click on "Windows Network" but then I get the same error wnen I click on the workgroup.

I followed the instructions in the Howto article entitled "Fix Windows Share browsing issues" ([http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)) until I got as far as "Problem 3 - Part 2",  and attempted to execute the command;
    ***sudo apt-get install winbind***

which resulted in the response;

[COLOR=Green]   [I]Reading package lists... Error!
   E: Encountered a section with no Package: header
   E: Problem with 
          MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
   E: The package lists or status file could not be parsed or opened.

[/I][/COLOR]I rebooted, but still got the same error.
I have pasted the contents of the file referenced in the error message ([COLOR=Green]*/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages*[/COLOR]) here;

[FONT=Arial][SIZE=1][COLOR=Green]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
   <head><title>Vodafone</title>
      <!--meta HTTP-EQUIV='Pragma' CONTENT='no-cache'-->
      <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
     
    <script type="text/javascript">
    <!-- 
    var ipaddr = '192.168.1.1';
    var language = 'en_US';
    var loc = 'http://'+ ipaddr + '/' + language + '/hspa/HspaFirstPage.html';
    window.location = loc;
    
    // done hiding -->
    </script>
   </head>
   <body>
     
   </body>
</html>[/COLOR][/SIZE][/FONT][SIZE=1]
[/SIZE]
Any ideas?

Thanks,
Pat

---

### Post by PaddyIndigo on 2011-07-28
Or to put it another way,  is it possible using 11.04 to join a Windows XP network?

---

### Post by PaddyIndigo on 2011-08-24
I finally got this sorted,  although i am not quite sure what actually fixed it. If you're reading this trying to solve a similar problem [click here for some info on what I did]("http://ubuntuforums.org/showthread.php?p=11161339#post11161339").

And my printer problem is sorted too,  but I had to kludge it a little, [see here]("http://ubuntuforums.org/showthread.php?t=1827127").

---

