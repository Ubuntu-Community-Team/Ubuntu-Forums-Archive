---
title: "please help!!!!! proxy problem....."
date: 2011-04-01
forum: New to Ubuntu
---

### Post by jagandecapri on 2011-04-01
i could not install or upgrade anything using the sudo apt-get.....

i have the errors as below.....
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jagandecapri@Jagatheesan:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                            
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Packages                                  
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Packages                                  
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Err [http://dl.google.com](http://dl.google.com) stable/main Packages                                  
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid Release 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates Release               
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Packages
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Sources
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://my.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

E: Some index files failed to download, they have been ignored, or old ones used instead.

```URGENT HELP NEEDED........:confused:

---

### Post by gmargo on 2011-04-01
To configure a proxy for the packaging system, edit (or create) **/etc/apt/apt.conf** to add a proxy specification like this, and substitute appropriately:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```

---

### Post by kdbruyne on 2011-04-02
> **gmargo said:**
> To configure a [proxy sites]("http://proxy-zone.net") for the packaging system, edit (or create) **/etc/apt/apt.conf** to add a proxy specification like this, and substitute appropriately:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```

Thanks that's what i was lookin for :o

---

