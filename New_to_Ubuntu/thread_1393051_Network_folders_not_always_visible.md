---
title: "Network folders not always visible"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by japhyr on 2010-01-28
Hello,

I have Ubuntu 8.04.3 installed on about ten computers in my classroom.  They are all set up to access a set of shared folders that live on a Windows network.  The username, workgroup, and password are set to "remember forever".  From any computer, we can get to the shared folders by opening Nautilus and typing "smb://shared_folder_name" in the location bar.

On some computers the shared folder is always visible.  For example when a student turns the computer on and opens a text editor, the shared folder shows up as an option in the "Save As" dialog.  For other computers the shared folder does not automatically show up.  Every time the computer is logged out and logged back in, the shared folders become invisible until someone goes through Nautilus and types in the location again.

Is there a way to make the shared folder visible on all the computers?

---

### Post by dmillerct on 2010-01-28
> **japhyr said:**
> Hello,

I have Ubuntu 8.04.3 installed on about ten computers in my classroom.  They are all set up to access a set of shared folders that live on a Windows network.  The username, workgroup, and password are set to "remember forever".  From any computer, we can get to the shared folders by opening Nautilus and typing "smb://shared_folder_name" in the location bar.

On some computers the shared folder is always visible.  For example when a student turns the computer on and opens a text editor, the shared folder shows up as an option in the "Save As" dialog.  For other computers the shared folder does not automatically show up.  Every time the computer is logged out and logged back in, the shared folders become invisible until someone goes through Nautilus and types in the location again.

Is there a way to make the shared folder visible on all the computers?

I had the same issue a while back. I just accessed the SMB share in nautilus and hit Control+D to bookmark it. It should always be visible as long as the server is up of course.

---

### Post by japhyr on 2010-01-29
Thank you, bookmarking worked.

---

