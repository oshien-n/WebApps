# Web Apps - Windows Server 2016
## Written by Oshien Nellissery

### Contact 
- Slack: **@oshien**
- Email: oshiennellissery@gmail.com

### Table of Contents

- [Prerequisites](#prereq)
- [Summary](#summary)
- [Downloading and Creating of Windows Server 2016](#windowsdownload)
- [Windows Server Setup](#windowssetup)
- [Installing IIS and CGI](#IIS&CGI)
- [Installing PHP](#PHP)
- [Configure IIS](#configureIIS)
- [Check PHP](#checkPHP)
- [Create PHP Website](#PHPwebsite)
- [Troubleshooting](#troubleshoot)

## Prerequisistes <a id="prereq"></a>
1. Have Ubuntu ISP running
2. Have Firewall running

## Summary <a id="summary"></a>
We will be setting up Windows Server 2016 in order to host a simple .php website.

## Downloading and Creating Windows Server 2016 <a id="windowsdownload"></a>
1. Download the Windows Server 2016 ISO from [here](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016#evaluation_4252). This version of WS is for evaluations and will expire after 180 days.
<p align="center">
  <img src="images/1.png?raw=true" alt="Windows Server Download"/>
</p>

2. Use the downloaded Windows Server ISO to create a Virtual Machine. Use the recommended setting for the allocated RAM, storage and CPU cores. VMWare users can follow these images. Virtual Box users can use the same setting but the GUI will look different. 
- Choose the Windows Server ISO
<p align="center">
  <img src="images/2.png?raw=true" alt="Choose ISO"/>
</p>

- Choose Microsoft Windows for Operating System and Windows Server 2016 for version
<p align="center">
  <img src="images/3.png?raw=true" alt="Choose System"/>
</p>

- Name the VM with any preferred name
<p align="center">
  <img src="images/4.png?raw=true" alt="Name VM"/>
</p>

- Allocate space for VM
<p align="center">
  <img src="images/5.png?raw=true" alt="VM space"/>
</p>

3. Boot the Windows Server Virtual Machine. 
<p align="center">
  <img src="/images/6.png?raw=true" alt="Boot"/>
</p>

## Windows Server Setup <a id="windowssetup"></a>
1. The following instructions will guide you through the Windows Setup Wizard. 
- Choose Language 
<p align="center">
  <img src="/images/7.png?raw=true" alt="Language"/>
</p>

- Click `Install` to begin
<p align="center">
  <img src="/images/8.png?raw=true" alt="Install"/>
</p>

- Select the `Windows Server 2016 Standard Evaluation (Desktop Experience)` 
<p align="center">
  <img src="/images/9.png?raw=true" alt="Choose Operating System"/>
</p>

- Accept the License Terms 
<p align="center">
  <img src="/images/10.png?raw=true" alt="License"/>
</p>

- Choose `Custom: Install Windows only (advanced)` option
<p align="center">
  <img src="/images/11.png?raw=true" alt="Custom Windows Install"/>
</p>

- Choose the virtual hard disk you have created to install Windows Server
<p align="center">
  <img src="/images/12.png?raw=true" alt="Hard Disk"/>
</p>

- Wait for Windows Server to finish installing
<p align="center">
  <img src="/images/13.png?raw=true" alt="Finish Install"/>
</p>
<p align="center">
  <img src="/images/14.png?raw=true" alt="Final Boot"/>
</p>

2. Configure Windows Server Admin account. 
- Choose a secure password for the Admin account
<p align="center">
  <img src="/images/15.png?raw=true" alt="Password"/>
</p>

- Sign-in to Windows Server by pressing `Ctrl+Atl+Delete` and typing in the Admin password you just created
<p align="center">
  <img src="/images/18.png?raw=true" alt="Login"/>
</p>

- Allow Windows Server to use reccomended setting for network
<p align="center">
  <img src="/images/20.png?raw=true" alt="Network"/>
</p>

- Launch Server Manager (if it doesn't launch automatically)
<p align="center">
  <img src="/images/21.png?raw=true" alt="Server Manager"/>
</p>

## Installing IIS and CGI <a id="IIS&CGI"></a>
1. Follow these insturctions to install IIS and CGI. Both of these are needed to host a PHP website. 
- Click `Add roles and Features`
<p align="center">
  <img src="/images/22.png?raw=true" alt="Add roles and features"/>
</p>

- Under `Server Roles` make sure that `Web Server (IIS)` is checked
<p align="center">
  <img src="/images/23.png?raw=true" alt="Server roles"/>
</p>
<p align="center">
  <img src="/images/24.png?raw=true" alt="IIS"/>
</p>

- Under `Confirmation` click `Install`
<p align="center">
  <img src="/images/25.png?raw=true" alt="Install"/>
</p>
<p align="center">
  <img src="/images/26.png?raw=true" alt="Installation"/>
</p>

- Close the Wizard and click `Add Roles and Features`
<p align="center">
  <img src="/images/27.png?raw=true" alt="Add roles and features"/>
</p>

- In the `Server Roles` tab, make sure the `CGI` box is checked (`Web Server IIS>Web Server>Application Development>CGI`)
<p align="center">
  <img src="/images/28.png?raw=true" alt="CGI"/>
</p>

- Under the `Confirmation` tab click `Install`
<p align="center">
  <img src="/images/29.png?raw=true" alt="Install"/>
</p>

## Installing PHP <a id="PHP"></a>
1. Download the latest .zip file from [http://windows.php.net/](http://windows.php.net/).
<p align="center">
  <img src="/images/30.png?raw=true" alt="PHP website"/>
</p>

2. Follow these instuctions to install PHP.
- Unzip the PHP .zip file that was previously downloaded and move it to `C:\` and rename the folder `PHP7`
<p align="center">
  <img src="/images/31.png?raw=true" alt="ZIP"/>
</p>

- Right click on `PHP7` in the `C:\` drive and click `Properties`. Under the `Security` tab click `Edit`. In the new window click `Add`. Cick `Advanced`. Next click `Find Now` and in the search results choose `IIS_IUSERS` and click `OK`. 
<p align="center">
  <img src="/images/32.png?raw=true" alt="IIS_IUSRS"/>
</p>
<p align="center">
  <img src="/images/33.png?raw=true" alt="OK"/>
</p>

- In the security window check the `Full control Allow` box. This will give the IIS user full control over PHP.
<p align="center">
  <img src="/images/34.png?raw=true" alt="Control"/>
</p>

- Under `C:\PHP7`, make a copy of the `php.ini-development` file and rename the copy `php.ini`
<p align="center">
  <img src="/images/35.png?raw=true" alt="Copy"/>
</p>

- Right click `Start` and go to `System`. In the System window, choose `Advanced system settings`. 
<p align="center">
  <img src="/images/36.png?raw=true" alt="System Settings"/>
</p>

- In the `System Properties` window, open `Environment Variables...`
<p align="center">
  <img src="/images/37.png?raw=true" alt="System Properties"/>
</p>

- Edit `System Variables` `Path` to add the new path; `C:\PHP7`
<p align="center">
  <img src="/images/38.png?raw=true" alt="System Variables"/>
</p>
<p align="center">
  <img src="/images/39.png?raw=true" alt="Path"/>
</p>
<p align="center">
  <img src="/images/40.png?raw=true" alt="C:\PHP7"/>
</p>

- Close all open windows

## Configure IIS <a id="configureIIS"></a>
1. In `Server Manager`, click `Tools` and open `IIS` (Internet Informtion Services).

- On the left `Connections` section, choose your server and click `Handler Mappings` under IIS
<p align="center">
  <img src="/images/41.png?raw=true" alt="Handler Mappings"/>
</p>

- Click `Add Module Mapping...` on the top right and use the configuration provided below to fill in the window
<p align="center">
  <img src="/images/42.png?raw=true" alt="Mapping"/>
</p>
<p align="center">
  <img src="/images/43.png?raw=true" alt="Configure"/>
</p>

- Back in the server home menu inside IIS, choose `Default Documentation` 
<p align="center">
  <img src="/images/44.png?raw=true" alt="Documentation"/>
</p>

- Choose the `Add...` action at the top right and name the default document `index.php`
<p align="center">
  <img src="/images/45.png?raw=true" alt="Add"/>
</p>
<p align="center">
  <img src="/images/46.png?raw=true" alt="index.php"/>
</p>

## Check PHP <a id="checkPHP"></a>
1. Run the command `php -info` inside Powershell and make sure you get a reply back with information, like the php license.
<p align="center">
  <img src="/images/47.png?raw=true" alt="powershell"/>
</p>

## Create PHP Website <a id="PHPwebsite"></a>
1. Open Notepad and enter the code `<?php phpinfo(); ?>` and Save As `phpinfo.php` (When saving, make sure to change file type to `All Files`). This file will create a PHP webpage showing information about the current PHP installation.
<p align="center">
  <img src="/images/48.png?raw=true" alt="Notepad"/>
</p>

- Move the `phpinfo.php` file to `C:\inetpub\wwwroot\` 
<p align="center">
  <img src="/images/49.png?raw=true" alt="inetpub"/>
</p>

2. Visit `http:\\localhost\phpinfo.php` to view the newly created PHP website.
<p align="center">
  <img src="/images/50.png?raw=true" alt="PHP website"/>
</p>

## Troubleshooting <a id="troubleshoot"></a>
**`php -info` doesn't reply with anything**
 
 -This means you are missing a .dll file necessary for PHP to run. Visit [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145) to download **Visual C++ Redistributable for Visual Studio 2015**. Be sure to download and install both **x64 and x86** versions. 
