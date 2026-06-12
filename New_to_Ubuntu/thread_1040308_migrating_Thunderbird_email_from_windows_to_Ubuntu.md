---
title: "migrating Thunderbird email from windows to Ubuntu"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-01-15
Thanks for any help.
Have created a folder called .mozilla-thunderbird and created another file in it called profiles.ini
When I click in home folder, view, show hidden files, look for .mozilla-thunderbird, expand and Right Click on profiles.ini, I am supposed to open that with a text editor and copy in the following:
   [general]
   StartWithLastProfile=1
   [profile0]
   name=default
   IsRelative=1
   path=gkfx983t.default
            |
        my module from Windows Thunderbird
   
I get an ERROR: profiles.ini is a directory
What in the devil does that mean??????

---

### Post by cariboo on 2009-01-15
The way I usually to it, is to start Thunderbird and then cancel when it wants me to create an account. This creates the ~/.mozilla-thunderbird directory. I then copy my xxxxxxx-default directory to ~/.mozilla-thunderbird and edit profile.ini to point to the just copied xxxxxxx-default directory.

Jim

---

### Post by rbo83 on 2009-01-20
Here is a shell script to automatically migrate any Windows version of Thunderbird and/or Firefox to Ubuntu, provided one of your drives contains a Windows partition. Make it executable using chmod. It must be run as 'root' :

# Script to migrate a Windows(All versions) Firefox or Thunderbird user to Ubuntu Linux
# Notes : 

# -Windows MUST have been 'Shutdown' normally, not 'Standby' or 'Hibernate',
#  Otherwise we will not be able to mount the Windows partition
# -The Owner and Group of the transfered files will be that of the Linux User
#  selected
# -The Windows-specific application extensions are not kept. They must be
#  re-installed in Linux
# -There is NO SELinux Security check
# -The script does not work for Virtualized Windows partitions

# If variable 'Test' has any value, no profile will be migrated, but all checks
# will be performed. Set it to '' if you do not want a test.
  Test=''

# Default variables, intended to be used in future script changes for other
# distributions than Ubuntu
  LinuxSystem=Ubuntu
# Where user durectories are stored
  LinuxRoot='/home'
# This is where we will mount the Windows partition
  MountDir='/mnt/my-windows'

  clear

  echo "Please select which application you wish to migrate from Windows to"
  echo "the $LinuxSystem system :"
  echo "1-) Thunderbird"
  echo "2-) Firefox"
  read aaa
  if [ "$aaa" = "1" ]; then
# Name of the application we are processing
    LinuxApplication='Thunderbird'
# Where the application data is located in $LinuxSystem
    LinuxAppDir='.mozilla-thunderbird'
# Where the application data is located in Windows
    WindowsAppDir='/Thunderbird'
  else
 
    if [ "$aaa" = "2" ]; then
# Name of the application we are processing
      LinuxApplication='Firefox'
# Where the application data is located in $LinuxSystem
      LinuxAppDir='.mozilla/firefox'
# Where the application data is located in Windows
      WindowsAppDir='/Mozilla/Firefox'
    else
      echo "Invalid selection ('$aaa') - Run cancelled."
      exit 1
    fi
  fi

  echo "You selected to migrate $LinuxApplication from Windows to $LinuxSystem."

#########################################################################
# Make sure only root can run our script
  if [[ $EUID -ne 0 ]]; then
     echo "This script must be run as root" 1>&2
     exit 1
  fi
  echo "This script will find and migrate your Windows $LinuxApplication data to $LinuxSystem" 
  echo ''

#########################################################################
# Function to find if user profiles exist on a multi-user Windows system
# Variables 'WindowsRoot' and 'WindowsTrail' must be pre-defined
# Exits with variable 'Windows_Profile' set to the directory name for 
# the first Windows user found, or empty if no user directory was found.
find_Windows_Profile() {

  Windows_Profile=''
  cd "$WindowsRoot"

# Change field separator so we don't have problems with spaces in filenames
  SAVIFS=$IFS
  IFS=$(echo -en "\n\b")

# This assumes each Windows user has a directory named after his/her userid
  users=`ls -d *`

# Scan directories for valid user profiles starting at $WindowsRoot
  for user in $users; do
    if [ -d "$user" ]; then
      if [ -e "$WindowsRoot/$user$WindowsTrail" ]; then
# Found a Windows user profile directory
        Windows_Profile=$user
      fi
    fi
  done
# Restore field separator
  IFS=$SAVIFS
  return 1    
}

#########################################################################
# Function to determine what Windows version is on a partition and get
# the proper directory where profiles are located in Windows.
# It sets the variables 'WindowsRoot', 'WindowsTrail', 'WindowsType' and
# 'WindowsUsers' to locate system user profiles depending on the Windows 
# version found.
# The partition to be checked must already be mounted on $MountDir

find_Windows_Version () {

# Check if it is single user Win95, 98 or ME
  WindowsRoot="$MountDir/windows"
  WindowsTrail="/Application Data$WindowsAppDir/Profiles"
  WindowsType='Win 95/98/ME'
  if [ -e "$WindowsRoot$WindowsTrail" ]; then
    Windows_Profile=''
    return 1
  fi

# Check if it is Multi-user Win95, 98 or ME
  WindowsRoot="$MountDir/windows/Profiles"
  WindowsTrail="/Application Data$WindowsAppDir/Profiles"
  WindowsType='Win 95/98/ME Multi-user'
  if [ -e "$WindowsRoot" ]; then
    find_Windows_Profile
    if [ "$Windows_Profile" != "" ]; then
      return 1
    fi
  fi

# Check if it is Win XP, 2000 or Server
# Note : This only deals with the first $LinuxApplication user found on Windows
  WindowsRoot="$MountDir/Documents and Settings"
  WindowsTrail="/Application Data$WindowsAppDir/Profiles"
  WindowsType='Win XP,2000,Server'
  if [ -e "$WindowsRoot" ]; then
    find_Windows_Profile
    if [ "$Windows_Profile" != "" ]; then
      return 1
    fi
  fi

# Check if it is an NT version
# Note : This only deals with the first $LinuxApplication user found on Windows
  WindowsRoot="$MountDir/WINNT/Profiles"
  WindowsTrail="/Application Data$WindowsAppDir/Profiles"
  WindowsType='Win NT'
  if [ -e "$WindowsRoot" ]; then
    find_Windows_Profile
    if [ "$Windows_Profile" != "" ]; then
      return 1
    fi
  fi

# Check if it is a Vista version
# Note : This only deals with the first $LinuxApplication user found on Windows
  WindowsRoot="$MountDir/Users"
  WindowsTrail="/AppData/Roaming$WindowsAppDir/Profiles"
  WindowsType='Win Vista'
  if [ -e "$WindowsRoot" ]; then
    find_Windows_Profile
    if [ "$Windows_Profile" != "" ]; then
      return 1
    fi
  fi

# Could not find a Windows $LinuxApplication profile
  WindowsRoot=''
  WindowsTrail=''
  WindowsDir=''
  WindowsType='Not Found'
  return 0
}

#########################################################################
# Function to copy a Windows profile to Linux. The following variables 
# must be pre-defined

copy_profile () {

# Ask user if this is the right Windows profile to copy
  echo ''
  echo "OK, on disk $Disk, we found a $WindowsType user '$WindowsUser' with a"
  echo "$LinuxApplication profile."
  echo "Is this the user you wish to migrate to $LinuxSystem ? (Y/N)"
  read aaa
  aaa=`echo $aaa | tr a-z A-Z`
  if [ "$aaa" != "Y" ]; then
    echo "Skipping $WindowsUser."
    return 0
  fi
# Switch directly to the specific user (or default) profile directory
  cd "$WindowsDir"
# List all profiles for this user
  WindowsProfile=`ls -d *.default`
  echo "OK, user '$WindowsUser' on $WindowsType has this $LinuxApplication profile:"
  echo "$WindowsDir/$WindowsProfile"
  echo ''
  echo "The following are the $LinuxSystem user(s) with a $LinuxApplication profile:"
  echo ''
  echo "$LinuxUsers"
  echo ''
  echo "Which $LinuxSystem user is to receive $WindowsUser's Windows $LinuxApplication files:"

  read LinuxUser
  if [ ! -d "$LinuxRoot/$LinuxUser/$LinuxAppDir" ]; then
    echo "That ($LinuxUser) was not a valid user. Please restart this program"
    cd ~/
    umount $MountDir
    exit 1
  fi

# Now get the Linux profile directory where we will copy Windows data
  cd "$LinuxRoot/$LinuxUser/$LinuxAppDir"
  LinuxProfile=`ls -d *.default`
  echo "We will now attempt to copy the Windows $LinuxApplication data for Windows user"
  echo "'$WindowsUser' to the following $LinuxSystem user '$LinuxUser' directory :"
  echo "$LinuxRoot/$LinuxUser/$LinuxAppDir/$LinuxProfile"
  echo ''

# Find out if this script was run previously
  if [ -e "$LinuxRoot/$LinuxUser/Windows2Linux/$LinuxProfile" ]; then
    echo "This program was run previously. So no back-up copy is required"
  else
    echo -n "Making a back-up copy of the $LinuxUser profile just in case..."
# Don't copy if this is just a test
    if [ "$Test" = "" ]; then
      mkdir -p "$LinuxRoot/$LinuxUser/Windows2Linux"
      chown $LinuxUser:$LinuxUser $LinuxRoot/$LinuxUser/Windows2Linux
      cd "$LinuxRoot/$LinuxUser/$LinuxAppDir"
      cp -pr * "$LinuxRoot/$LinuxUser/Windows2Linux"
      echo Done
    else
      echo ''
      echo "This is just a test, no copies are made"
    fi
  fi

  echo ''
  echo -n "Copying Windows $LinuxApplication data to $LinuxSystem..."
# Don't copy if this is just a test
  if [ "$Test" = "" ]; then
    cd "$WindowsDir/$WindowsProfile"
    cp -pr * "$LinuxRoot/$LinuxUser/$LinuxAppDir/$LinuxProfile"
    echo Done
# Eliminate any Windows extensions in the selected profile by overwriting them
# with the default $LinuxSystem installation extensions.
    cd "$LinuxRoot/$LinuxUser/Windows2Linux/$LinuxProfile"
    echo 'Clearing Windows extensions...'
    cp -p extensions.* "$LinuxRoot/$LinuxUser/$LinuxAppDir/$LinuxProfile"
    chown -R $LinuxUser:$LinuxUser $LinuxRoot/$LinuxUser/$LinuxAppDir/$LinuxProfile
    echo "You can now start $LinuxApplication on $LinuxSystem and check if all is ok"
    echo "All of your Windows data is still available"
  else
    echo ''
    echo "This is just a test, no copies are made"
  fi
  echo "Migration of Windows user '$WindowsUser' to $LinuxSystem user '$LinuxUser' complete"
  return 1
}

#########################################################################
# Find out which users $LinuxApplication is installed for on Linux
# Assume it is a $LinuxSystem default installation

  echo -n "Scanning $LinuxSystem users..."
  
  cd $LinuxRoot
# Change field separator so we don't have problems with spaces in filenames
  SAVIFS=$IFS
  IFS=$(echo -en "\n\b")
  LinuxUsers=`ls -d *`
  concat=''
  for i in $LinuxUsers; do
    if [ -d "$LinuxRoot/$i/$LinuxAppDir" ]; then
      cd "$LinuxRoot/$i/$LinuxAppDir"
      prof=`ls -d *.default`
      if [ "$prof" != "" ]; then
        if [ "$concat" = "" ]; then
          concat="$i"
        else
          concat="$concat,$i"
        fi
      fi
    fi
  done
# Restore field separator
  IFS=$SAVIFS

  if [ "$concat" = "" ]; then
    echo ''
    echo "Either $LinuxApplication is not installed on $LinuxSystem or"
    echo "you have not yet started it to create a default profile."
    echo "Either install $LinuxApplication, if it is not, or start"
    echo "$LinuxApplication in $LinuxSystem and then exit. This will create"
    echo "a default profile we will use to migrate your Windows version"
    echo ''
    echo 'Migration NOT successful'
    exit 1
  fi
# Store the list of users with a $LinuxApplication profile on Linux
  LinuxUsers=$concat
  echo 'Done'

#########################################################################
# Find any IDE or SCSI disks on the system
  echo 'Scanning disks on your system... '
  MountDir='/mnt/my-windows'
  mkdir -p $MountDir
  for i in hda hdb hdc sda sdb sdc; do
    if [ -e "/dev/$i" ]; then
      for W in ntfs fat32; do
        Part=`parted "/dev/$i" print | grep "$W" | sed 's/  .*//' | sed 's/ //g'`
        if [ "$Part" != "" ]; then
          echo "Found a Windows $W partition on disk '$i$Part'. Looking for users..."
          Disk="/dev/$i$Part"
# Windows partition $W found on drive $i partition $Part
          Part_Type=ntfs
          if [ "$W" = "fat32" ]; then
            Part_Type=vfat
          fi
# Mount the partition Windows partition so we can scan it
          mount -t $Part_Type "$Disk" $MountDir
# Make sure it contains Windows user profiles...
          find_Windows_Version
          if [ "$WindowsRoot" != "" ]; then
# Scan for Windows users
            cd "$WindowsRoot"

# ------------------ Single user Windows processing ----------------------
            if [ "$Windows_Profile" = "" ]; then
              WindowsDir="$WindowsRoot$WindowsTrail"
# THere is no user name directory for single user systems. Assume 'Default'
              WindowsUser='Default'
              copy_profile

# ------------------ Multi user Windows processing -----------------------
            else
# Change field separator so we don't have problems with spaces in filenames
              SAVIFS=$IFS
              IFS=$(echo -en "\n\b")
# This assumes each Windows user has a directory named after his/her userid
              users=`ls -d *`
# Scan directories for valid user profiles starting at $WindowsRoot
              for user in $users; do
                if [ -d "$WindowsRoot/$user" ]; then
                  if [ -e "$WindowsRoot/$user$WindowsTrail" ]; then
# Found a Windows user profile directory
                    WindowsUser=$user
                    WindowsDir="$WindowsRoot/$WindowsUser$WindowsTrail"
# Found a Windows profile directory to be copied to Linux
                    copy_profile
                  fi
                fi
              done
# Restore field separator
              IFS=$SAVIFS
            fi
          fi
          cd ~/
          umount $MountDir
        fi
      done
    fi
  done
# Cleanup after ourselves
  rmdir $MountDir
  echo 'End of migration program'

---

