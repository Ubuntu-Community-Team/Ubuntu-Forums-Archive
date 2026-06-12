---
title: "Partition Erased Grub2?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-06-05
I have fixed grub, but I was wondering why when I partitioned my 160GB HD setup to dual boot vista and Ubuntu, why it erased the MBR? And any advice on how to safely make the Ubuntu partition larger from shrinking the windows partition? I know you can shrink, but I couldnt add the extra space to Ubuntu. (These are all on one laptop HD) 

I was mostly wondering why its rewrote the MBR? I used Easeus Partition Manager, and it restarted the computer and booted into its own bootloader. Could it be after it was finished it replace the Windows MBR?

I had windoes vista installed first, then I installed Ubuntu with 7GB and needed more space. So I used Easeus Partition Manager in windows and shrunk the windows partition. Then I tried to add that space to Ubuntu with Easeus, and then I tried Gparted. This is all on an installed version of Ubuntu.

---

### Post by rraj.be on 2010-06-05
When ever windows is installed in any machine, it will over write the MBR with its own bootloader i believe. Please correct me if its wrong.

---

### Post by wilee-nilee on 2010-06-05
> **walkerchuckwalker said:**
> I have fixed grub, but I was wondering why when I partitioned my 160GB HD setup to dual boot vista and Ubuntu, why it erased the MBR? And any advice on how to safely make the Ubuntu partition larger from shrinking the windows partition? I know you can shrink, but I couldnt add the extra space to Ubuntu. (These are all on one laptop HD) 

I was mostly wondering why its rewrote the MBR? I used Easeus Partition Manager, and it restarted the computer and booted into its own bootloader. Could it be after it was finished it replace the Windows MBR?

You might tell us in what order you installed and what is happening now as far as booting. Also it sounds like your trying to either run gparted from the OS or not turning off swap when using gparted from the live CD, always partition with a live Cd or one that will load to ram like partmagic.

The description of the MBR being erased makes no sense without more information.

I recognize you haven't referenced gparted, you can't shrink widows of any kind and have it do anything more the leave a open unallocated space, which from a live Ubuntu cd can be expanded into with the swap off.

---

