---
title: "need oracle database 10g build on ubuntu linux."
date: 2009-10-23
forum: New to Ubuntu
---

### Post by venkat24 on 2009-10-23
Hi All,
         I have downloaded oracle 10g build but it is applicable to red hat,opensuse but not for ubuntu 9.04.Kindly help me in getting exact oracle 10g database build for ubuntu 9.04.


Thanks in advance.

Venkat

---

### Post by Mighty_Joe on 2009-10-23
It doesn't look like there is one:

> 
Oracle provides the following for Linux server deployments: patches, fixes, updates, and back ports for RHEL3, RHEL4 and RHEL5, delivered via a subscriber network, the Unbreakable Linux Network (ULN):

    * Red Hat Enterprise Linux 5 Server and Advanced Platform: Oracle offers full support for RHEL 5 on x86 and x86-64, and ia64 (ia64 forward from Update 4) architectures certified by Red Hat.
    * Oracle Enterprise Linux 5 images for installation (ISOs) are available at [http://linux.oracle.com](http://linux.oracle.com)
    * Red Hat Enterprise Linux 4 AS/ES: Oracle offers full support for RHEL4 and later on x86, x86-64, and ia64 (ia64 forward from Update 6) architectures certified by Red Hat.
    * Oracle Enterprise Linux 4: EL4 images for installation (x86, x86-64, ia64(from Update 6 forward)) (ISOs) are available at [http://linux.oracle.com](http://linux.oracle.com)
    * Red Hat Enterprise Linux 3 AS/ES: Oracle's support for RHEL3 on x86 and x86-64 architectures certified by Red Hat is limited to existing customers' installations. Oracle does not provide operating system images for installation (ISOs), but does provide bug fixes.
    * Red Hat Enterprise Linux Workstation Edition: Oracle does not support the WS editions of RHEL.
[Metalink Document 266043.1]("https://metalink.oracle.com/metalink/plsql/ml2_documents.showDocument?p_database_id=NOT&p_id=266043.1")

---

### Post by ukripper on 2009-10-23
> **venkat24 said:**
> Hi All,
         I have downloaded oracle 10g build but it is applicable to red hat,opensuse but not for ubuntu 9.04.Kindly help me in getting exact oracle 10g database build for ubuntu 9.04.


Thanks in advance.

Venkat

You better off using CENTOS/REDHAT with oracle than with ubuntu. Why don't you use MYSQL setup with Ubuntu in first place?

---

### Post by Waappu on 2009-10-28
Hi,

Oracle XE comes with DEB package. Of course it is not full version and have some limitations
[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

If you search from Google, you can find many instructions how install "full" version to Ubuntu.

> **ukripper said:**
> You better off using CENTOS/REDHAT with oracle than with ubuntu. Why don't you use MYSQL setup with Ubuntu in first place?

I like Oracle database because there is nice feature called Application Express.
[http://www.oracle.com/technology/products/database/application_express/index.html](http://www.oracle.com/technology/products/database/application_express/index.html)

---

### Post by ukripper on 2009-10-28
> **Waappu said:**
> 

I like Oracle database because there is nice feature called Application Express.
[http://www.oracle.com/technology/products/database/application_express/index.html](http://www.oracle.com/technology/products/database/application_express/index.html)

Depends on what you use it for. In many cases it would be overkill to use Oracle DB

---

