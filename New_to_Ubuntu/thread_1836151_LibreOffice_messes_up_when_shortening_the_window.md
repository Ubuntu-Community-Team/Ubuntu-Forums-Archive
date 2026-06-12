---
title: "LibreOffice messes up when shortening the window"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by WubiAR on 2011-08-30
Hi,

I am using Xubuntu 11.04 Natty stable. When I drag the window with the size adjustment tool to the top right of LibreOffice, I can see that the application becomes smaller. However, it also takes out the menu and whatever else was in that space before. How could I fix this problem?

A screenshot will be provided upon request.

---

### Post by ajgreeny on 2011-08-30
> **WubiAR said:**
> Hi,

I am using Xubuntu 11.04 Natty stable. When I drag the window with the size adjustment tool to the top right of LibreOffice, I can see that the application becomes smaller. However, it also takes out the menu and whatever else was in that space before. How could I fix this problem?

A screenshot will be provided upon request.
What "size adjustment tool"?  Do you mean the normal manner of resizing with the window borders, or is this tool specific to xubuntu?

---

### Post by brdmn on 2011-09-09
I'm having this issue as well.  Resizing by grabbing the window borders with the mouse seems to shrink the window, but all the contents, including the menu are "off" the window.  The application is definitely not frozen, because I can move around the cells that are visible, and keyboard shortcuts like F5 work.

Here's a workaround: If you right-click the application in the panel, select "maximize", and then "unmaximize", the window is restored.

---

### Post by derekh4 on 2012-09-12
There is a workaround that fixes this bug.  From "Synaptic Package Manager" install the package named "libreoffice-gtk" and restart any LibreOffice windows.  This will fix this issue.

From the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/889212](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/889212)

---

