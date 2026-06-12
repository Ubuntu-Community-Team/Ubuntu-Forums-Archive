---
title: "Problem installing openssh-server"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by jimmy-j on 2007-12-31
I'm attempting to install openssh-server onto a new build of 7.10  64amd.  
I've tried "sudo apt-get install openssh-server" and get the error message "Package openssh-server is not available, but is referred to by another package.  this may mean that the package is missing , has been obsoleted or is available from another source."
When I try "sudo aptitude install openssh-server" I receive the message "No candidate version found for openssh-server.  No packages will be installed."
I then tried to install from "http://packages.umbuntu.com/dapper/net/openssh-server" and receive the error message in red "Error - Dependency is not satisfiable: openssh-client".  but when I look with the Snaptic Package Manager, I see both the packages openssh-client and openssh are loaded.

Any help would be really appreciated!

Thanks

---

### Post by PilotJLR on 2008-01-01
try this
```

sudo apt-get update
sudo apt-get install openssh-server

```

---

### Post by jimmy-j on 2008-01-01
Thanks for the suggestion.  But when I tried it, I got the same response as before "Package openssh-server is not available, but is referred . . ."

Jimmy-J

---

