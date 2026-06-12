---
title: "Can not Logout anymore?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by tommo12 on 2009-05-26
Everytime I go to logout it comes up with a blank screen, I am not sure if this has been caused by the new ATI Cat driver i installed the other day, but could be... any ideas?

---

### Post by stephanvaningen on 2009-05-26
Can you start terminal and do:
```
dmesg | tail
```
and put the output of that in the thread here?

---

### Post by tommo12 on 2009-05-26
[ 3726.299711] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[ 3726.299716] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[ 3818.570964] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[ 3818.570970] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[ 3846.049619] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[ 3846.049625] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[ 3884.703827] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[ 3884.703833] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[ 3932.085649] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[ 3932.085655] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is



thats what it came up with

---

### Post by stephanvaningen on 2009-05-26
Did you start encryption of folders during this session? If so, which folders?

---

### Post by tommo12 on 2009-05-26
um... not that I know of... I am pretty new to ubuntu, the only encryption option i have seen is in installing ubuntu, which i said yes too and when u start up for the first time it mentions it too but i closed that window... I have been trying to install vmware without success dunno if that has done something...

---

