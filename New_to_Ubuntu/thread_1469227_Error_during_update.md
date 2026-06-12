---
title: "Error during update"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by liusha on 2010-05-02
Hi all,

I am a beginner of Ubuntu Forum. These days, I frequently got a few errors while updating. But I don't know where to post this. So I put it here. Could any give me some help?
following is the output of "sudo apt-get update". 
I am in Singapore, so the server I choose was [http://fpt.science.nus.edu.sg](http://fpt.science.nus.edu.sg). But it seems that when I was installing the system, I select my region was US.
------------------------------------------------------------------------
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid Release.gpg
Ign [http://ftp.science.nus.edu.sg/ubuntu/](http://ftp.science.nus.edu.sg/ubuntu/) lucid/main Translation-en_US
Ign [http://ftp.science.nus.edu.sg/ubuntu/](http://ftp.science.nus.edu.sg/ubuntu/) lucid/universe Translation-en_US
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-updates Release.gpg
Ign [http://ftp.science.nus.edu.sg/ubuntu/](http://ftp.science.nus.edu.sg/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://ftp.science.nus.edu.sg/ubuntu/](http://ftp.science.nus.edu.sg/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-security Release.gpg
Ign [http://ftp.science.nus.edu.sg/ubuntu/](http://ftp.science.nus.edu.sg/ubuntu/) lucid-security/main Translation-en_US
Ign [http://ftp.science.nus.edu.sg/ubuntu/](http://ftp.science.nus.edu.sg/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid Release            
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-updates Release    
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-security Release   
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid/main Packages      
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid/universe Packages  
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-updates/main Packages
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-updates/universe Packages
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-security/main Packages
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-security/universe Packages
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid/main Packages      
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid/universe Packages  
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-updates/main Packages
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-updates/universe Packages
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-security/main Packages
Ign [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-security/universe Packages
Err [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid/main Packages      
  404  Not Found
Err [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid/universe Packages  
  404  Not Found
Err [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-updates/main Packages
  404  Not Found
Err [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-updates/universe Packages
  404  Not Found
Err [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-security/main Packages
  404  Not Found
Err [http://ftp.science.nus.edu.sg](http://ftp.science.nus.edu.sg) lucid-security/universe Packages
  404  Not Found
W: Failed to fetch [http://ftp.science.nus.edu.sg/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ftp.science.nus.edu.sg/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ftp.science.nus.edu.sg/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://ftp.science.nus.edu.sg/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ftp.science.nus.edu.sg/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://ftp.science.nus.edu.sg/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ftp.science.nus.edu.sg/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://ftp.science.nus.edu.sg/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ftp.science.nus.edu.sg/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://ftp.science.nus.edu.sg/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ftp.science.nus.edu.sg/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://ftp.science.nus.edu.sg/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
--------------------------------------------------------------------------------------

---

### Post by Elfy on 2010-05-02
moved to ABT - try changing the server [http://ubuntuforums.org/showpost.php?p=9212079&postcount=2](http://ubuntuforums.org/showpost.php?p=9212079&postcount=2)

You have a different issue than that - but the way to change the server remains the same.

---

