---
title: "Shared Folder Issue"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by cult hero on 2007-01-10
I'm not quite sure where to post this (I'm relatively new to this forum and Ubuntu, but not Linux) but this seems like as good a place as any.

I installed Ubuntu for the first time the other night primarily because I wanted Linux to "just work." Thus far it's been a pretty good experience and I'm very impressed with the polish of this distro. I'm trying to document what I see as "quirks" for someone coming from the Windows world as I go since it is my hope to migrate a few people I know from Windows to Linux.

Like Windows I can simply right click a folder and go to "share." I also really like the "shared folders" option under Administration that gives me a list of all the active shares. Excellent stuff.

The problem I ran into, and perhaps I missed something simple, is that while making a share was easy, I couldn't access them from another machine. I'd get a prompt for a username and password but my own didn't work. The problem seems to be that passwd and smbpasswd aren't linked in any way. While this was no problem for me (I just opened up a command line and added my users via smbpasswd) I didn't see any way to do this from the GUI and people coming from a Windows machine don't have to set a password for shares separately.

Is there a package or an option or a GUI tool or something for this? I did a little forum searching but the consensus seemed a little unclear. Are they supposed to be linked and not due to a bug or something?

---

