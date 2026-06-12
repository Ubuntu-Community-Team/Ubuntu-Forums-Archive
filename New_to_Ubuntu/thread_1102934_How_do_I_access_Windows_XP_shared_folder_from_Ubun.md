---
title: "How do I access Windows XP shared folder from Ubuntu on the same network?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by amylase on 2009-03-22
As title, thanks.

I have two Windows XP computers and a Ubuntu computer all connected to the same ADSL modem/router at home. One of the XP computers has its folder set for sharing. The other XP computer can happily access the shared folder already. How do I access that shared folder from my Ubuntu computer?

Thanks.

---

### Post by llamabr on 2009-03-22
Are you running samba?

---

### Post by fabricator4 on 2009-03-22
> **amylase said:**
> As title, thanks.

I have two Windows XP computers and a Ubuntu computer all connected to the same ADSL modem/router at home. One of the XP computers has its folder set for sharing. The other XP computer can happily access the shared folder already. How do I access that shared folder from my Ubuntu computer?

Thanks.

Install Samba - in terminal type:
sudo apt-get install samba

This will let you see the windows workgroup.  Click on:

Places -->  Network

This should show an Icon called "Windows Network".  Double click on it and you should see an Icon with your workgroup name.  Double click on that and you should see all the shares on that workgroup.  If you mount the share (right click and mount volume) then that share will appear in the "Places" drop down menu and should stay there until it is unmounted.

Chris.

---

### Post by blandman3 on 2009-03-22
do you have to unmount those files before exiting ubuntu?

---

### Post by fabricator4 on 2009-03-22
> **blandman3 said:**
> do you have to unmount those files before exiting ubuntu?

No you don't, and they should still be there next time boot.

Chris

---

### Post by blandman3 on 2009-03-22
> **fabricator4 said:**
> Install Samba - in terminal type:
sudo apt-get install samba

This will let you see the windows workgroup.  Click on:

Places -->  Network

This should show an Icon called "Windows Network".  Double click on it and you should see an Icon with your workgroup name.  Double click on that and you should see all the shares on that workgroup.  If you mount the share (right click and mount volume) then that share will appear in the "Places" drop down menu and should stay there until it is unmounted.

Chris.

I followed the steps, but I guess I am missing something because what I get is a message stating:

failed: unable to mount share

---

