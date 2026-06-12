---
title: "Help with repository indexes"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by LilmissLinux on 2009-02-04
Im having trouble updating my linux hardy system.  it keeps giving me this message:[FONT="Arial"

]Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.[/FONT]

I tried changing the server to another one but none of the servers are active.  THis is also a dell mini from the UK and so I noted before I changed it, that it was on a UK server recieving updates just fine.

Help

---

### Post by mistypotato on 2009-02-04
I had that issue but it was because a firewall was blocking the sites.

The IP looks valid.

I had to add ALL of ubuntu's IP addresses for the conical server to my list of sites that were NOT blocked.

Good luck.

---

### Post by LilmissLinux on 2009-02-04
iM not very computer oriented...how do i get the ip's from the sites and do i have to manually unblock each address from my firewall

---

