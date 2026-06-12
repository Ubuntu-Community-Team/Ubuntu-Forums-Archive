---
title: "How do I clean up my &quot;Applications&quot; menu?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-09-13
I have been having a lot of trouble with WINE and it's apps for a long time, now cleared up more or less all thanks to help from guys on the forum.

I have one more thing I'd like to clear up.

I have uninstalled all WINE files and everything associated with them. But my "Applications" menu still shows wine and other stuff. Please help me to get rid of the residual menu entries.

This is what my ```
~/.config/menus/applications.menu
``` looks like

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Accessibility</Name>
		<Include>
			<Filename>orca.desktop</Filename>
		</Include>
		<AppDir>/home/dad/.local/share/applications</AppDir>
		<Deleted/>
	</Menu>
	<Menu>
		<Name>Multimedia</Name>
		<AppDir>/home/dad/.local/share/applications</AppDir>
		<Exclude>
			<Filename>gnome-volume-control.desktop</Filename>
		</Exclude>
		<DirectoryDir>/home/dad/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Menu>
		<Name>System</Name>
		<DirectoryDir>/home/dad/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
		<Menu>
			<Name>wine-Programs</Name>
			<Menu>
				<Name>wine-Programs-Watchtower Library 2008</Name>
				<AppDir>/home/dad/.local/share/applications</AppDir>
				<Include>
					<Filename>wine-Programs-Watchtower Library 2008-Watchtower Library 2008 - English.desktop</Filename>
				</Include>
			</Menu>
			<Menu>
				<Name>wine-Programs-Watchtower Library 2007</Name>
				<AppDir>/home/dad/.local/share/applications</AppDir>
				<Include>
					<Filename>wine-Programs-Watchtower Library 2007-Watchtower Library 2007 - Français.desktop</Filename>
				</Include>
			</Menu>
			<Menu>
				<Name>wine-Programs-IMVConverter</Name>
				<Exclude>
					<Filename>wine-Programs-IMVConverter-Uninstall IMVConverter.desktop</Filename>
				</Exclude>
				<AppDir>/home/dad/.local/share/applications</AppDir>
				<Include>
					<Filename>wine-Programs-IMVConverter-IMVConverter.desktop</Filename>
				</Include>
			</Menu>
		</Menu>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<AppDir>/home/dad/.local/share/applications</AppDir>
		<Exclude>
			<Filename>wine.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>wine-extension-rtf.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-extension-wtfav.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-extension-html.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-extension-wri.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-extension-hlp.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-extension-htm.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-extension-xml.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Internet</Name>
		<AppDir>/home/dad/.local/share/applications</AppDir>
		<Include>
			<Filename>epiphany.desktop</Filename>
		</Include>
		<Include>
			<Filename>Google Earth.desktop</Filename>
		</Include>
		<Layout>
			<Merge type="menus"/>
			<Filename>amaya.desktop</Filename>
			<Filename>evolution-mail.desktop</Filename>
			<Filename>firefox.desktop</Filename>
			<Filename>firestarter.desktop</Filename>
			<Filename>grsync.desktop</Filename>
			<Filename>Google Earth.desktop</Filename>
			<Filename>kde4-knetattach.desktop</Filename>
			<Filename>LimeWire.desktop</Filename>
			<Filename>thunderbird.desktop</Filename>
			<Filename>pidgin.desktop</Filename>
			<Filename>vinagre.desktop</Filename>
			<Filename>skype.desktop</Filename>
			<Filename>sun-java5-javaws.desktop</Filename>
			<Filename>sun-java6-javaws.desktop</Filename>
			<Filename>tsclient.desktop</Filename>
			<Filename>transmission.desktop</Filename>
			<Merge type="files"/>
		</Layout>
	</Menu>
	<Menu>
		<Name>Accessories</Name>
		<Exclude>
			<Filename>gworldclock.desktop</Filename>
		</Exclude>
		<AppDir>/home/dad/.local/share/applications</AppDir>
	</Menu>
</Menu>

I just want to get rid of everything to do with WINE so that I can do a nice clean reinstallation of it.

Thanks many for your help.

---

### Post by fooman on 2009-09-13
have you tried right-clicking on applications and choosing "edit menus"?

when the main menu pops up,  look in the left column for "wine"...click on it once to highlight,  then press the "delete" button over on the right.

---

### Post by running_rabbit07 on 2009-09-13
System>Preferences>Main Menu?

---

### Post by tahitiwibble on 2009-09-13
> **fooman said:**
> have you tried right-clicking on applications and choosing "edit menus"?

when the main menu pops up,  look in the left column for "wine"...click on it once to highlight,  then press the "delete" button over on the right.

I tried this and the WINE stuff just won't go away.

---

### Post by tahitiwibble on 2009-09-13
> **running_rabbit07 said:**
> System>Preferences>Main Menu?

^^^ WOW, it just did! Thanks so much. Why didn't it work when I went to right-click "Edit Menus"? and why is all the info still in the "applications.menu" file? 

But thanks again, it's been driving me crazy.

---

