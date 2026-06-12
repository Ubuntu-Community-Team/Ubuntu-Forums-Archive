---
title: "ARG! I don't know what I did!!"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by staplerz on 2007-01-28
I just got Ubuntu about 5 hours ago and i successfully installed it on my new PC 4 hours ago. I really like the interface and everything about it. After awhile of just snooping around on it I decided try and set up the internet. So i went under..."System/Administrator/Networking" on the top menu. I added all the correct information needed (eg. DNS, IP...) I am using a router and I assumed i had to change the host name. So i changed the host namer to the name of my router. When i pressed OK/Apply/Save(i don't remember which one) it said that if i changed the host name some programs might not be able to run. Not thinking i pressed okay. Now every time i try to go back under the Networking Setting a Bug buddy window appears with this error:

[COLOR="Red"]Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0
Memory status: size: 29335552 vsize: 0 resident: 29335552 share: 0 rss: 11157504 rss_rlim: 0
CPU usage: start_time: 1169944074 rtime: 0 utime: 23 stime: 0 cutime:22 cstime: 0 timeout: 1 it_real_value: 0 frequency: 0
Backtrace was generated from '/usr/bin/network-admin' 
(no debugging symbols found)                
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".   
        
(no debugging symbols found)         
     ^***^ It does that 49 more times
    
[Thread debugging using libthread_db enabled]     
[New Thread -1225120080 (LWP 7233)]      
   
(no debugging symbols found)               
     ^***^ It does that 28 more times

0xffffe410 in __kernel_vsyscall ()        
#0  0xffffe410 in __kernel_vsyscall ()      
#1  0xb73b6323 in __waitpid_nocancel ()           
from /lib/tls/i686/cmov/libpthread.so.0             
#2  0xb7f491b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0               
#3  <signal handler called>
#4  0xb7668b92 in g_slice_free_chain_with_offset ()
from /usr/lib/libglib-2.0.so.0
#5  0xb764f891 in g_list_free () from /usr/lib/libglib-2.0.so.0 
#6  0x08050ba7 in ?? ()                    
 #7  0x082415a0 in ?? ()                     
#8  0x0804e4dc in gtk_combo_box_set_active_iter@plt ()                     
#9  0x00000000 in ?? ()                                         
Thread 1 (Thread -1225120080 (LWP 7233)):                     
#0  0xffffe410 in __kernel_vsyscall ()                     
No symbol table info available.                    
 #1  0xb73b6323 in __waitpid_nocancel ()                        
from /lib/tls/i686/cmov/libpthread.so.0                     
No symbol table info available.                     
#2  0xb7f491b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0                     
No symbol table info available.                     
#3  <signal handler called>                     
No symbol table info available.                    
 #4  0xb7668b92 in g_slice_free_chain_with_offset ()                        
from /usr/lib/libglib-2.0.so.0                     
No symbol table info available.                     
#5  0xb764f891 in g_list_free () from /usr/lib/libglib-2.0.so.0                     
No symbol table info available.                     
#6  0x08050ba7 in ?? ()                     
No symbol table info available.                     
#7  0x082415a0 in ?? ()                     
No symbol table info available.                     
#8  0x0804e4dc in gtk_combo_box_set_active_iter@plt ()                     
No symbol table info available.                     
#9  0x00000000 in ?? ()                    
 No symbol table info available.                     
#0  0xffffe410 in __kernel_vsyscall ()                     
                     [/COLOR]


Can some one help me because i have no idea what happened and I'm completely new to Linux and Ubuntu. I was reading up on what happened to me and someone said to try  to change the host name in the terminal by using "hostname" I tried it and it just gives me this error: "Hostname: You must be root to change the host name"
Im sooo confused.

---

### Post by raul_ on 2007-01-28
Try logging out and in again. The host name is just the name of the computer

---

### Post by staplerz on 2007-01-28
> **raul_ said:**
> Try logging out and in again. The host name is just the name of the computer

I have. I've restarted and everything. I even tried to do the "Recover" thing on the OS cd.

---

### Post by raul_ on 2007-01-28
See if this is related:

[http://www.ubuntuforums.org/showthread.php]("http://www.ubuntuforums.org/showthread.php")

---

### Post by staplerz on 2007-01-28
> **raul_ said:**
> See if this is related:

[http://www.ubuntuforums.org/showthread.php]("http://www.ubuntuforums.org/showthread.php")

This is all it says.

"No Thread specified. If you followed a valid link, please notify the administrator"

---

### Post by staplerz on 2007-01-28
Okay i got it to work!! woot!
all i had to do is "sudo network-admin" 
If this happens to anyone els look at this post.
[http://ubuntuforums.org/showthread.php?t=312391&highlight=Network+Settings+bug+buddy](http://ubuntuforums.org/showthread.php?t=312391&highlight=Network+Settings+bug+buddy)

---

### Post by raul_ on 2007-01-28
Ups. I don't know what happened, sorry. That was the solution that was in that thread though. Glad you got it working

---

