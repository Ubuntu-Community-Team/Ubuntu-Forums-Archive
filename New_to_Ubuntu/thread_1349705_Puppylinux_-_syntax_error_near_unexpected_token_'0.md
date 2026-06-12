---
title: "Puppylinux - syntax error near unexpected token '0'"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by Spartukus on 2009-12-08
Hey guys keep having problems with the below script syntax error near unpexpected token '0' exit 0
 
I have two directorys backups and Usr in the usr i have sub dir's wp,ss,pic which i would like to back up (copy those directorys to the backups directory) with user acknowledgement from command line. I would then want the ability to restore those files back to the Usr from Backups so the code is below if any one could be so kind to help me out, would be much appreciated.
 
Thanks 
-----------------------------------------------------------------------------------------
echo "please choose backup or restore"
read bor
 
case "$bor" in
 
backup )
ls -d Usr/*
echo "please choose directory to backup (example wp,ss,pic)"
read dir
 
case "$dir" in
 
wp )
echo "word processor directory backedup"
cp -r Usr/wp Backups/wp;;
 
ss )
echo "word processor directory backedup"
cp -r Usr/ss Backups/ss;;
 
pic )
echo "word processor directory backedup"
cp -r Usr/pic Backups/pic;;
 
restore )
ls -d Backups/*
echo "please choose directory to restore (wp,ss,pic)"
read bdir
 
case "$bdir" in
 
wp )
echo "word processor directory restored"
cp -r Backups/wp Usr/wp;;
 
ss )
echo "word processor directory restored"
cp -r Backups/ss Usr/ss;;
 
pic )
echo "word processor directory restored"
cp -r Backups/pic Usr/pic;;
 
exit 0

---

