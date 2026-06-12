---
title: "Runtime.getruntime.exec, not working in tomcat 6 using wicket 1.4.17"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by arjay12 on 2011-06-11
Hi ...  I'm just a newbie here and I have a question 
I'm doing a project about handling lxc containers using wicket 1.4.17 and tomcat6 and the code is this...


import org.apache.wicket.markup.html.form.Form;

import DataAccessObject.Container;
import DataAccessObject.User;
import Model.LXCContainer;
import View.AddContainerPage;
import View.ContainersPage;

public class AddContainerForm extends Form{
	private Container LXCContainer;
	private User user;
	private LXCContainer LXCContainerModel;
	public AddContainerForm(String id){
		super(id);
	}
	public void onSubmit(){
		 user = new User();
		 LXCContainer = new Container();
		 LXCContainerModel = new LXCContainer();
		 user.setUsername(AddContainerPage.getContainerOwner());	 LXCContainer.setContainerName(AddContainerPage.getContainerName());		 LXCContainer.setIPAdd(AddContainerPage.getContainerIPAdd());		 LXCContainer.setGateway(AddContainerPage.getContainerGateWay());		 LXCContainer.setBroadcast(AddContainerPage.getContainerBroadcast());		 LXCContainer.setNetmask(AddContainerPage.getContainerNetmask());		 LXCContainer.setContainerNetworkIpv4(AddContainerPage.getContainerNetworkIpv4());
LXCContainer.setEthernetConnection(AddContainerPage.getContainerEthernetConnection());
LXCContainerModel.createContainer(user, LXCContainer);
setResponsePage(ContainersPage.class);
	}
}	

then I created a separate class that will handle the request

import DataAccessObject.Container;
import DataAccessObject.User;

public class LXCContainer {
	private DataBase myDB;
	private BufferedReader reader;
	private String processIndicator = null;
	private RuntimeProcess runtimeProcess;
public void createContainer(User user,Container LXCContainer){
createDataBase();
initRuntimeProcess();
String CreateContainerCommand = "ShellScripts/createContainer.sh " + LXCContainer.getContainerName() + " " + LXCContainer.getEthernetConnection()+" "+LXCContainer.getIPAdd()+" "+LXCContainer.getNetmask()+" "+LXCContainer.getBroadcast()+" "+LXCContainer.getGateway()+" "+LXCContainer.getContainerNetworkIpv4();			
			
Process CreateContainerProcess = runtimeProcess.startProcessof(CreateContainerCommand);				runtimeProcess.getInputStreamof(CreateContainerProcess);
myDB.createContainer(user, LXCContainer);
	}
}


and then for the runtime class....


package Model;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class RuntimeProcess {
	private BufferedReader buffer;
	private String processIndicator;
	public Process startProcessof(String command){
		try {
			return Runtime.getRuntime().exec(command);
		} catch (IOException e) {
			e.printStackTrace();
		}
		return null;
	}
	public void getInputStreamof(Process createContainerProcess){
                buffer = new BufferedReader(new InputStreamReader(createContainerProcess.getInputStream()));
		try {
			while((processIndicator = buffer.readLine()) != null){
				System.out.println(processIndicator);
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
		
	}
	public void getErrorStreamof(Process process){
		buffer = new BufferedReader(new InputStreamReader(process.getErrorStream()));
		try {
			processIndicator = buffer.readLine();
			while(processIndicator != null)
			System.out.println(processIndicator);
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}

when I used my test cases it did fine but when I deployed it in tomcat it did nothing just the setResponsePage ... even the line 
myDB.createContainer(user, LXCContainer) was not executed.
anything you can help about this matter? .... 


and by the way the shell script is this : 

#!/bin/bash
sudo mkdir /var/lib/lxc/$1
sudo tar xzvf /home/lucid/workspace/LinuxContainer/src/Model/DefaultContainer/DefaultContainer.tar.gz -C /var/lib/lxc/$1
sudo chmod 777 /var/lib/lxc/$1/rootfs/etc/network/interfaces
sudo chmod 777 /var/lib/lxc/$1/config
sudo echo 'auto '$2 >> /var/lib/lxc/$1/rootfs/etc/network/interfaces
sudo echo 'iface '$2' inet static' >> /var/lib/lxc/$1/rootfs/etc/network/interfaces
sudo echo 'address '$3 >> /var/lib/lxc/$1/rootfs/etc/network/interfaces
sudo echo 'netmask '$4 >> /var/lib/lxc/$1/rootfs/etc/network/interfaces
sudo echo 'broadcast '$5 >> /var/lib/lxc/$1/rootfs/etc/network/interfaces
sudo echo 'gateway '$6 >> /var/lib/lxc/$1/rootfs/etc/network/interfaces
sudo echo 'lxc.rootfs = /var/lib/lxc/'$1'/rootfs' >> /var/lib/lxc/$1/config
sudo echo 'lxc.utsname = '$1 >> /var/lib/lxc/$1/config
sudo echo 'lxc.network.name = '$2 >> /var/lib/lxc/$1/config
sudo echo 'lxc.network.ipv4 = '$7 >> /var/lib/lxc/$1/config

and it is already set to executable....

---

