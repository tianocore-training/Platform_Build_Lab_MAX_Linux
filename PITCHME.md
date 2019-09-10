---?image=assets/images/gitpitch-audience.jpg
@title[Platform Build MAX Lab Linux]
<br><br>
<br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

Platform Build Lab MinnowBoard Max - Linux

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  Platform Build Lab MAX Windows

  Copyright (c) 2019, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]

### <p align="center"<span class="gold"   >Platform Build Labs </span></p>
<span style="font-size:0.9em">Lab Setup and Build for Minnowboard Max/Turbot</span> <br>
<br>
<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp; Hardware Setup for Minnowboard Max/Turbot </span><br><br>
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp; Build a EDK II Platform using Minnowboard <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Max/Turbot </span> <br><br>
  

---?image=assets/images/binary-strings-black2.jpg
@title[Setup MAX HW Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Platform HW Setup</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Setup hardware for MinnowBoard Max/Turbot </span>

---?image=/assets/images/slides/Slide4.JPG
@title[MAX/Turbot HW]
### <p align="right"><span class="gold" >EDK II Platform (MinnowBoard MAX/Turbot)</span></p>
@snap[south-west span-45 ]
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.6em" >Intel<sup>&reg;</sup> Atom processor E3800 Series<br> &lpar;Formerly Bay Trail-I&rpar;</span></p>
<br>
@snapend
Note:

This lab shows the build process for an actual platform – Minnowboard.org

- Using Tianocore source
- Open source EDK II plus open source binary obj. packages

---?image=/assets/images/slides/Slide5.JPG
@title[Workshop Lab Hardware]
### <p align="right"><span class="gold" >MinnowBoard  MAX Workshop Lab Hardware</span></p>
@snap[south span-100 ]
<br>
<p style="line-height:80%" ><span style="background-color: #FFFFFF; font-size:0.60em; "> <font color="red">&nbsp;<b>**Warning</b> do not use any other power supply than 5V or the board will Fry&nbsp;&nbsp;</font></span></p>
<br>
@snapend
Note:

**Warning do not use any other power supply than 5V or the board will Fry


---?image=/assets/images/slides/Slide6.JPG
@title[Install Screen on Ubuntu]
<p align="right"><span class="gold" >@size[1.1em](<b>Install "Screen" on Ubuntu&nbsp;&nbsp;&nbsp;&nbsp;  </b>)</span>
<span style="font-size:0.55em;" ><br> - skip for Clear Linux* Project &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  </span></p>

@snap[north-west span-51 ]
<br>
<br>
<br>
<br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:60% "><span style="font-size:0.5em;" ><br><br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.780em;  " >
 Terminal prompt (Cnt-Alt-T)</span></p>
<p style="line-height:45%" align="left" > <span style="font-size:0.57em; font-family:Consolas;" ><br>
&nbsp;&nbsp; bash$ sudo apt-get install screen &nbsp;&nbsp;<br>
&nbsp;&nbsp; bash$ cd $Home &nbsp;&nbsp;<br>
&nbsp;&nbsp; bash$ gedit ~.screenrc &nbsp;&nbsp;
</span></p>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.780em;  " >
Inside the editor, type<br> @size[.8em]("<font face="Consolas">shell /bin/bash</font>") &nbsp;&nbsp;then save
</span></p>
<br>
@snapend

@snap[north-east span-42 ]
<br>
<br>
<br>
<br>
<p style="line-height:50%" align="left"><span style="font-size:0.60em;  " >
 <font color="#87E2A9"> While in screen<br>
 <b>Cnt-A</b> then <b>D</b> goes back to Terminal
 <br></font><br>
 @size[.9em](<font face="Consolas">bash$ screen -r</font>) <br>
 (Returns to screen)
</span></p>
 <br>
@snapend



@snap[south-east span-80 ]
<p style="line-height:60%" align="left"><span style="font-size:0.560em;  " >
Skip if using Clear Linux* Project, Screen already install<br>
There may be other serial terminal applications that are supported. 
</span></p>
@snapend

Note:
- Terminal prompt (Cnt-Alt-T)<br>
`bash$ sudo apt-get install screen`<br>
`bash$ cd $Home`<br>
`bash$ gedit ~.screenrc`


` shell /bin/bash`

Click Save


---?image=/assets/images/slides/Slide7.JPG
@title[Max Test System]
<p align="right"><span class="gold" >@size[1.1em](<b>Setup MinnowBoard Max Test System  </b>)</span>
<span style="font-size:0.75em;" >  </span></p>


@snap[north-west span-60 ]
<br>
<br>
<br>
<p style="line-height:50%"><span style="font-size:0.7em"><b>Hardware:</b></span></p>
<ul style="list-style-type:none; line-height:0.6;">
  <li><span style="font-size:0.5em">- System Under Test (SUT) - MinnowBoard Max/Turbot  </span>  </li>
  <li><span style="font-size:0.5em">- USB to 3.3V TTL Cable  (6 pin to USB Type A) </span>  </li>
  <li><span style="font-size:0.5em">- 5V power supply </span>  </li>
</ul>
<p style="line-height:50%"><span style="font-size:0.6em">
Connect the USB w/ 6 pin header to SUT (MAX) <br>
&nbsp;&nbsp;&nbsp;- black wire (pin 1) is closest to the SATA connector<br><br>
Connect the USB Type A connector to Host (Laptop) <br><br>
</span></p>
<br>
@snapend

@snap[south span-100 ]
<br>
<p style="line-height:80%" ><span style="background-color: #FFFFFF; font-size:0.560em; "> <font color="red">&nbsp;<b>**Warning</b> do not use any other power supply than 5V or the board will Fry&nbsp;&nbsp;</font></span></p>
@snapend

Note:
	
- Hardware:
- System Under Test (SUT) – MinnowBoard Max or Turbot
- 5V- ** power supply
- USB to 3.3V TTL Cable  (6 pin to USB Type A)
  - Connect the USB w/ 6 pin header to SUT
     -  black wire(pin 1) is closest to the SATA connector
  - Connect the USB Type A connector to Host

---?image=/assets/images/slides/Slide8.JPG
@title[Max Test System 02]
<p align="right"><span class="gold" >@size[1.1em](<b>Setup MinnowBoard Max Test System  </b>)</span><span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.780em;  " >
 Open Terminal prompt (Cnt-Alt-T)<br>
 <br>
 <font face="Consolas"><span style="background-color: #000000; font-size:0.60em;"> 
&nbsp;&nbsp; bash$ sudo dmesg &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>
&nbsp;&nbsp; bash$ sudo chmod 666 /dev/ttyUSB@color[cyan](<i>n</i>) &nbsp;&nbsp;
</span></font>
</span></p>
<br>
@snapend

@snap[north-east span-52 ]
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.60em;  " >
 <br>
 <br>
 (to check which USB port is assigned)<br>
 (where @color[cyan](<i>n</i>) is the FTDI number ) &nbsp;&nbsp;
</span></p>
<br>
@snapend

Note:

- Open Terminal Prompt (Cnt-Alt-T)
```
bash$ sudo dmesg                     	#(to check which USB port is assigned)
bash$ sudo chmod 666 /dev/ttyUSBn	#(where n is the FTDI number)
```
- dmesg command  shows which - ttyUSBn


---?image=/assets/images/slides/Slide9.JPG
@title[Power on MinnowBoard MAX]
<p align="right"><span class="gold" >@size[1.1em](<b>Power on MinnowBoard MAX  </b>)</span>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:80%" align="left"><span style="font-size:0.80em;  " >
 Connect the Power supply cable to the MinnowBoard  MAX <br>
 <font face="Consolas"><span style="background-color: #000000; font-size:0.650em;"> 
&nbsp;&nbsp; bash$ screen /dev/ttyUSB@color[cyan](<i>n</i>) 115200 &nbsp;&nbsp;
</span></font><br>
@size[.8em](MinnowBoard MAX should boot to the UEFI Shell in the Terminal – Screen)
</span></p>
<br>
@snapend

@snap[north-east span-25 ]
<br>
<br>
<br>
<br>
<br>
<br>
<p style="line-height:50%" align="left"><span style="font-size:0.560em;  " >
 <br>
 <br>
 @color[yellow](While in Screen<br> <b>Cnt-A</b> then <b>D</b> goes back to terminal.)<br>
 <br>
 <font face="Consolas"><span style="background-color: #000000; font-size:0.90em;"> 
&nbsp;&nbsp; bash$ screen-r &nbsp;&nbsp;
</span></font><br> 
(returns to Screen)
  &nbsp;&nbsp;
</span></p>
<br>
@snapend




Note:
- Connect the Power supply cable to the MinnowBoard  MAX
```
bash$ screen /dev/ttyUSBn 115200
```
- MinnowBoard MAX should boot to the UEFI Shell in the Terminal – Screen .

- While in screen  Cnt-A then D goes back to terminal
```
 bash$ screen –r #(returns to screen)
```
- Note: Cnt-H for Backspace

**Warning do not use any other power supply than 5V or the board will Fry


---?image=assets/images/gitpitch-audience.jpg
@title[End of Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;End of Lab </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; @fa[chevron-right gp-bullet-cyan]  &nbsp;&nbsp;to continue  </span>
 

---?image=assets/images/binary-strings-black2.jpg 
@title[Lab 3 -Build Max/Turbot Section]
<br><br><br><br><br>
## <p align="center"><span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Build MinnowBoard Turbot</span></p>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>


---?image=/assets/images/slides/Slide4.JPG
@title[MAX/Turbot HW]
### <p align="right"><span class="gold" >EDK II Platform (MinnowBoard MAX/Turbot)</span></p>
@snap[south-west span-45 ]
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.6em" >Intel<sup>&reg;</sup> Atom processor E3800 Series<br> &lpar;Formerly Bay Trail-I&rpar;</span></p>
<br>
@snapend
Note:

-  Intel® Atom processor E3800 Series  (Formerly Bay Trail-I)


---?image=/assets/images/slides/Slide13.JPG
@title[MinnowBoard MAX/ Turbot Platform]
<br>
<p align="left"><span class="gold" ><b>Where to get Open Source<BR> MinnowBoard Max</b></span></p>

@snap[north-west span-60  ]
<br>
<br>
<br>
<br>
<br>
<ul style="list-style-type:disc; line-height:0.85;">
 <li><span style="font-size:0.8em;" > Open Source <a href="https://github.com/tianocore/tianocore.github.io/wiki/MinnowBoardMax">Max Development Wiki</a> </span> <br></li>
 <li><span style="font-size:0.8em;" > How to Download  & Build: <a href="https://github.com/tianocore/edk2-platforms/blob/master/Platform/Intel/Vlv2TbltDevicePkg/Readme.md">Readme.md</a> </span> </li>

</ul>
@snapend

Note:
- Step by step if NOT downloading Lab release of Minnowboard MAX/Turbot 

---
@title[Download MinnowBoard MAX Lab Source]
### <p align="right"><span class="gold" >Download MAX Lab Source</span></p>
<span style="font-size:0.9em" >Download the PlatformBuildLab2_FW.zip from : </span> @fa[github gp-bullet-white] <span style="font-size:0.7em"><a href="https://github.com/tianocore-training/PlatformBuildLab2_FW/archive/master.zip">github.com PlatformBuildLab_FW.zip</a></span><br>
<br>
<span style="font-size:0.9em" >OR<br>Use <font face="Consolas">git clone</font> to download the PlatformBuildLab2_FW<span>
```
$ git clone https://github.com/tianocore-training/PlatformBuildLab2_FW.git
```
<span style="font-size:0.9em" >Directory PlatformBuildLab2_FW will be created</span>
```
   FW 
    - PlatformBuildLab
       - MaxWS                                  - Minnowboard Max Source 
	   - . . .
```

Note:

---
@title[Linux setup for MinnowBoard Max Lab]
<p align="right"><span class="gold" >@size[1.1em](<b>Linux setup for MinnowBoard Max Lab  </b>)</span><span style="font-size:0.75em;" >  </span></p>
<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" ><br><br><br>
Lab Setup Requirements – Ubuntu 16.04
</span></p>
```
bash$ sudo apt-get install build-essential uuid-dev iasl git gcc-5 nasm 
bash$ sudo apt-get install screen
bash$ sudo apt-get install gcab 

```
<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" ><br><br><br><br>
Lab Setup Requirements – Clear Linux* Project
</span></p>
```
bash$ sudo swupd bundle-add devpkg-util-linux
bash$ sudo swupd bundle-add devpkg-gcab

```


@snap[north-west span-8]
<br>
![ubuntu](/assets/images/ubuntu-logo.png )
@snapend


@snap[west span-18]
<br>
<br>
![Clear-logo](/assets/images/ClearLinux-logo.png )
@snapend


Note:

---?image=/assets/images/slides/Slide16.JPG
@title[Copy MinnowBoard Max Source]
<p align="right"><span class="gold" >@size[1.1em](<b>Copy Minnowboard Max Source  </b>)</span>
<span style="font-size:0.75em;" >  </span></p>


@snap[north-west span-100 ]
<br>
<p style="line-height:70%"><span style="font-size:0.8em"><br>
Open a terminal prompt(Alt-Cnt-T)<br>
Create a working  space source directory under the home directory<br>
</span>
 <font face="Consolas"><span style="background-color: #000000; font-size:0.60em;"> 
&nbsp;&nbsp; bash$ mkdir ~src &nbsp;&nbsp;&nbsp;&nbsp;
</span></font><br>
<span style="font-size:0.65em">
From the <font face="Consolas">FW/PlatformBuildLab</font> folder, copy and paste folder <font face="Consolas">"~/../FW/MaxWS" to ~src</font>
</span></p>

@snapend


Note:
- Open a terminal prompt  (Alt-Cnt-T)
- Create a working  space source directory under the home directory
   - bash$ mkdir ~src
- From the FW/PlatformBuildLab folder, copy and paste folder “~FW/Max” to ~src
 

---?image=/assets/images/slides/Slide17.JPG
@title[Get the BaseTools]
<p align="right"><span class="gold" >@size[1.1em](<b>Get the BaseTools for Max   </b>)</span><br>

@snap[north-west span-51 ]
<br>
<br>
<br>
<br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:60% "><span style="font-size:0.5em;" ><br><br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:70%"><span style="font-size:0.8em">
Rename or <b>mv</b> the directory @size[.8em]("<font face="Consolas">~src/MaxWS/edk2/BaseTools</font>")
</span></p>
<p style="line-height:45%" align="left" ><span style="font-size:0.57em; font-family:Consolas;" ><br>
&nbsp;&nbsp; bash$ cd ~src/Max/edk2 &nbsp;&nbsp;&nbsp;&nbsp;<br>
&nbsp;&nbsp; bash$ mv BaseTools BaseToolsX &nbsp;&nbsp;<br>
&nbsp;&nbsp; bash$ tar -xf BaseToolsMax.tar.xz &nbsp;&nbsp;
</span></p>
<p style="line-height:70%"><span style="font-size:0.7em"><br>
Extract the file <font face="Consolas">@size[.7em](~src/MaxWS/edk2/BaseToolsMax.tar.xz)  to  @size[.7em](~src/MaxWS/edk2)</font>
</span></p>
@snapend

Note:

-  Extract the Rename or mv the directory “~src/MaxWS/edk2/BaseTools”
```
 bash$ cd ~src/MaxWS/edk2<Br>
 bash$ mv BaseTools BaseToolsxx
```

- Extract the file ~FW/PlatformBuildLab/BaseToolsMax.tar.gz  to  ~src/Max/edk2
  - bash$ tar -xf BaseToolsMax.tar.xz 
  


---
@title[Platform Source Directory Structure]
<p align="right"><span class="gold" >@size[1.1em](<b>Platform Source Directory Structure   </b>)</span>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:65%" align="left" ><span style="font-size:0.6em; font-family:Consolas;" >
./MaxWs/ <br>&nbsp;&nbsp;
	edk2/<br>&nbsp;&nbsp;&nbsp;&nbsp;
       <font face="Arial">@size[.8em](&lpar;EDK II common packages&rpar;)</font><br>&nbsp;&nbsp;&nbsp;&nbsp;
		BaseTools/<br>&nbsp;&nbsp;
	edk2-platforms/<br>&nbsp;&nbsp;&nbsp;&nbsp;
       Platform/Intel/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
		   Vlv2TbltDevicePkg /<br>&nbsp;&nbsp;&nbsp;&nbsp;
 	   Silicon/Intel/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          Vlv2DeviceRefCodePkg/<br>&nbsp;&nbsp;
	edk2-non-osi/<br>&nbsp;&nbsp;
	<br>&nbsp;&nbsp;
	<br>&nbsp;&nbsp;
<br><br><br>&nbsp;
</span></p>

@snapend


@snap[north-east span-88  fragment]
<br>
<br>
<p style="line-height:65%" align="left" ><span style="font-size:0.6em; font-family:Consolas;" >
<br>
@color[yellow](&#10094;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;&horbar;)
<span style="background-color: #64205d">&nbsp;&nbsp;<font face="Arial">Invoke the Build from here </font> &nbsp;&nbsp;</span><br>&nbsp;&nbsp;&nbsp;&nbsp;
<br>&nbsp;&nbsp;&nbsp;&nbsp;
<br>&nbsp;&nbsp;
<br>&nbsp;&nbsp;&nbsp;&nbsp;
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[yellow](&#10094;&horbar;&horbar;&horbar;&horbar;)
<span style="background-color: #64205d">&nbsp;&nbsp;<font face="Arial">Platform DSC here </font> &nbsp;&nbsp;</span><br>&nbsp;&nbsp;&nbsp;&nbsp;
</span></p>

@snapend




Note:
-  Platform Source Directory Structure
   -  Build from /Vlv2TbltDevicePkg  directory


---
@title[Steps to Build & Install Firmware]
<p align="right"><span class="gold" >@size[1.1em](<b> Steps to Build & Install Firmware </b>)</span><span style="font-size:0.75em;" >  </span></p>
<br>
<ul style="list-style-type:none; line-height:0.95;">
  <li><span style="font-size:0.8em">@size[1.0125em](<font color="yellow"> &#10102;</font>)&nbsp; Open Terminal prompt &  Cd <font face="Consolas">~/src/MaxWS</font>  </span></li>
  <li><span style="font-size:0.8em">@size[1.0125em](<font color="yellow"> &#10103;</font>)&nbsp; Set up local build environment, <font face="Consolas">edksetup.sh</font> </span></li>
  <li><span style="font-size:0.8em">@size[1.0125em](<font color="yellow"> &#10104;</font>)&nbsp; Build <font face="Consolas">"BaseTools" </font> </span></li>
  <li><span style="font-size:0.8em">@size[1.0125em](<font color="yellow"> &#10105;</font>)&nbsp; Invoke the build process (DEBUG & RELEASE) </span></li>
  <li><span style="font-size:0.8em">@size[1.0125em](<font color="yellow"> &#10106;</font>)&nbsp; Locate build output (.cap files for BIOS image)</span></li>
  <li><span style="font-size:0.8em">@size[1.0125em](<font color="yellow"> &#10107;</font>)&nbsp; Flash capsule image onto the platform</span></li>
  <li><span style="font-size:0.8em">@size[1.0125em](<font color="yellow"> &#10108;</font>)&nbsp; Reset & boot new firmware to UEFI Shell</span></li>
</ul>
<br>
<br>
<br>
<span style="font-size:0.9em"><font color="yellow"><i><b>Next slides will follow the above steps</b></i></font></span>


Note:

Slide says it all



---
@title[Setup the Build Environment]
<p align="right"><span class="gold" >@size[1.1em](<b>Setup the Build Environment</b>)</span></p>

@snap[north-west span-100 ]
<br>
<br>
<p style="line-height:45%" align="left" ><span style="font-size:0.40em; font-family:Consolas;" >&nbsp;&nbsp;<br><br><br><br></span></p>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:40% "><span style="font-size:0.9em;" ><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>&nbsp;</span></p>)
@snapend


@snap[north-west span-100 ]
<p style="line-height:80%" align="left"><span style="font-size:0.8em"><br>
<br>@size[1.0125em](<font color="yellow"> &#10102;</font>)&nbsp;&nbsp;Terminal prompt (Cnt-Alt-T)  & CD to work space directory <br>
<br>@size[1.0125em](<font color="yellow"> &#10103;</font>)&nbsp;&nbsp;Set up Local environment (PACKAGES_PATH)
</span></p>
<p style="line-height:40%" align="left" ><span style="font-size:0.47em; font-family:Consolas;" ><br>&nbsp;&nbsp;
bash$ cd ~src/MaxWS<br>&nbsp;&nbsp;
<br>&nbsp;&nbsp;
bash$ export WORKSPACE=$PWD<br>&nbsp;&nbsp;
bash$ export PACKAGES_PATH=$WORKSPACE/edk2:\<br>&nbsp;&nbsp;&nbsp;&nbsp;
$WORKSPACE/edk2-platforms/Silicon/Intel:\<br>&nbsp;&nbsp;&nbsp;&nbsp;
$WORKSPACE/edk2-platforms/Platform/Intel:\<br>&nbsp;&nbsp;&nbsp;&nbsp;
$WORKSPACE/edk2-non-osi/Silicon/Intel<br>&nbsp;&nbsp;
<br>&nbsp;&nbsp;
bash$ cd edk2/<br>&nbsp;&nbsp;
bash$ chmod +x edksetup.sh<br>&nbsp;&nbsp;
<br>&nbsp;&nbsp;
bash$ . edksetup.sh
</span></p> 

@snapend

Note:


---?image=/assets/images/slides/Slide21.JPG
@title[Building BaseTools]
<p align="right"><span class="gold" >@size[1.1em](<b>Building BaseTools</b>)</span></p>

@snap[north-west span-38 ]
<br>
<p style="line-height:45%" align="left" ><span style="font-size:0.40em; font-family:Consolas;" >&nbsp;&nbsp;<br><br></span></p>
<br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:40% "><span style="font-size:0.9em;" ><br><br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100 ]
<p style="line-height:80%" align="left"><span style="font-size:0.8em">
<br>@size[1.125em](<font color="yellow"> &#10104;</font>)<br><br>
&nbsp;&nbsp;Run Make
</span></p>
<p style="line-height:40%" align="left" ><span style="font-size:0.47em; font-family:Consolas;" >&nbsp;&nbsp;
bash$ cd ~/src/MaxWS/edk2<br>&nbsp;&nbsp;
bash$ make –C BaseTools/
</span></p>
<br>
<br>
<br>
<br>
<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" >
Make sure the tests pass OK
</span></p>
@snapend


Note:

---
@title[Platform Build Scripts]
<p align="right"><span class="gold" >@size[1.1em](<b>Platform Build Scripts</b>)</span></p>

@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:70%" align="center"><span style="font-size:0.8em">Platform Pre & Post Build Scripts<br>&nbsp; </span></p>)
<p style="line-height:80%"><span style="font-size:0.8em">Many Platforms have a bash, bat  or Python script file to pre or post process the EDK II build process</span></p>

<p style="line-height:60%"><span style="font-size:0.6em">@size[1.1em](For MinnowBoard MAX :)<br> 
@color[cyan](Pre build proecssing:)<br>
Python script <font face="Consolas">Vlv2TbltDevicePkg/@color[yellow](PreBuild.py) </font>– determines date and creates <font face="Consolas">BiosId.bin</font> in build output directory<br>
<br>
@color[cyan](Post build processing:) <br>
Python script <font face="Consolas">Vlv2TbltDevicePkg/Feature/Capsule/GenerateCapsule/ @color[yellow](GenCapsuleAll.py)</font> – creates .CAP files for updating<br>
</span></p>

Note:

For the platform edk II builds usually a script is called that will do pre and post build processing.  
There is also this capability that is part of the .dsc but many developers have not taken advantage of this feature


---?image=/assets/images/slides/Slide23.JPG
@title[Build Process for DEBUG]
<p align="right"><span class="gold" >@size[1.1em](<b>Build Process for DEBUG Target</b>)</span></p>

@snap[north-west span-100 ]
<p style="line-height:45%" align="left" ><span style="font-size:0.40em; font-family:Consolas;" >&nbsp;&nbsp;<br><br></span></p>
<br>
<br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:40% "><span style="font-size:0.9em;" ><br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100 ]
<p style="line-height:20%" align="left"><span style="font-size:0.8em">
<br><br><br>@size[1.0125em](<font color="yellow"> &#10105;</font>) 
</span></p>
<p style="line-height:70%" align="left"><span style="font-size:0.7em">
From the edk2/ directory invoke the “build” command to build MinnowBoard Max
</span></p>
<p style="line-height:35%" align="left" ><span style="font-size:0.41em; font-family:Consolas;" >&nbsp;&nbsp;
bash$ build -a IA32 -a X64 -t GCC5 -p Vlv2TbltDevicePkg/PlatformPkgX64.dsc –y Vlv.report -v
</span></p>
@snapend


@snap[south-east span-22 ]
<p style="line-height:37%" align="left" ><span style="font-size:0.55em;" >
Press Enter to <br>
Continue the build
<br>
<br>
</span></p>
@snapend

Note:

- From the terminal prompt


<pre>
bash$ cd C:\FW\MaxWS\edk2
bash$ build -a IA32 -a X64 -t GCC5 -p Vlv2TbltDevicePkg/PlatformPkgX64.dsc –y Vlv.report -v
</pre>


Vlv2TbltDevicePkg/PlatformPkgX64.dsc  is the MinnowBoard MAX DSC FILE

---
@title[Examine Command Line & Build Parameters]
<p align="right"><span class="gold" >@size[1.1em](<b>Examine Build Parameters</b>)</span></p>

@snap[north-west span-100 ]
<br>
<br>
@box[bg-black text-yellow rounded my-box-pad2  ](<p style="line-height:60%" align="left"><span style="font-size:0.65em; font-family:Consolas; " >&nbsp;&nbsp;build<br><br>&nbsp;&nbsp;</span></p>)
@snapend


@snap[north-east span-85  fragment]
<br>
<br>
<p style="line-height:60%" align="left"><span style="font-size:0.60em; font-family:Consolas; " >
<font color="#75deFF">
-a IA32 -a X64 -t GCC5 <br>-p Vlv2TbltDevicePkg/PlatformPkgX64.dsc -y Vlv.report -v
</font>
</span></p>
@snapend




@snap[north-west span-100 fragment ]
<br>
<br>
<br>
<br>
<br>
<table id="recTable">
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>TARGET</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](DEBUG)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Build Mode</b> (default)</span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>TARGET_ARCH</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](IA32 X64)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><b>CPU Architecture</b></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>TOOL_CHAIN_TAG</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](GCC5)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><b>Tool Chain</b></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>ACTIVE_PLATFORM</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:040%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](Vlv2TbltDevicePkg /PlatformPkgX64)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" ><b>MAX Platform DSC file</b></span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:040%"><span style="font-size:0.460em; font-family:Consolas; " ><b>Report File Created</b></span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " ><b>= @color[yellow](Vlv.report)</b></span></p></td>
		<td align="left" bgcolor="#0070C0" height=".0025" width="35%"><p style="line-height:010%"><span style="font-size:0.6em" ><b>PCDs, Libs, etc. . .</b></span></p></td>
	</tr>
</table>


@snapend

---
@title[Examine Platform Parameters]
<p align="right"><span class="gold" >@size[1.1em](<b>Platform Build and PCD Parameters</b>)</span></p>

@box[bg-purple-pp text-white rounded my-box-pad2  ](<p style="line-height:70%" align="center"><span style="font-size:0.8em">Platform Parameters<br>&nbsp; </span></p>)
<p style="line-height:80%"><span style="font-size:0.8em">Many Platform Parameters are defined in  a top .DSC file that controls  PCD and build switches</span></p>

<p style="line-height:70%"><span style="font-size:0.7em">For MinnowBoard MAX : <font face="Consolas">PlatformPkgConfig.dsc</font> <br>Example:</span></p>

```xml
 #
 # TRUE is ENABLE. FALSE is DISABLE.
 #
  //  . . .
 DEFINE SECURE_BOOT_ENABLE = TRUE
 DEFINE USER_IDENTIFICATION_ENABLE = FALSE
 DEFINE VARIABLE_INFO_ENABLE = FALSE
 DEFINE S3_ENABLE = TRUE
 DEFINE CAPSULE_ENABLE = TRUE
 DEFINE CAPSULE_RESET_ENABLE = TRUE
  // . . .

```

Note:

many will have "ifdef" statements in the major .dsc file in order to enable a feature or not


---?image=/assets/images/slides/Slide26.JPG
@title[Build Process for Release]
<p align="right"><span class="gold" >@size[1.1em](<b>Build Process for RELEASE Target</b>)</span></p>

@snap[north-west span-100 ]
<p style="line-height:45%" align="left" ><span style="font-size:0.40em; font-family:Consolas;" >&nbsp;&nbsp;<br><br></span></p>
<br>
<br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:40% "><span style="font-size:0.9em;" ><br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100 ]
<p style="line-height:20%" align="left"><span style="font-size:0.8em">
<br><br><br>@size[1.0125em](<font color="yellow"> &#10105;</font>) 
</span></p>
<p style="line-height:70%" align="left"><span style="font-size:0.7em">
From the edk2/ directory invoke the “build” command to build MinnowBoard Max
</span></p>
<p style="line-height:35%" align="left" ><span style="font-size:0.41em; font-family:Consolas;" >&nbsp;&nbsp;
bash$ build -a IA32 -a X64 -t GCC5 -b @color[yellow](RELEASE) -p Vlv2TbltDevicePkg/PlatformPkgX64.dsc  -v
</span></p>
@snapend

@snap[south-east span-20 ]
<p style="line-height:37%" align="left" ><span style="font-size:0.55em;" >
Press Enter to 
Continue the build
<br>
<br>
</span></p>
@snapend



Note:
From  Prompt enter:
```
bash$ cd ~/src/MaxWS/edk2
bash$ build -a IA32 -a X64 -t GCC5 -b RELEASE -p Vlv2TbltDevicePkg/PlatformPkgX64.dsc -v
```

---
@title[DEBUG & RELEASE Differences]
### <p align="right"><span class="gold" >DEBUG & RELEASE Differences</span></p>

@box[bg-purple-pp text-white rounded my-box-pad2 fragment](<p style="line-height:70%"><span style="font-size:0.9em" >Slower boot because the time it takes to display debug info <br>&nbsp; </span></p>)
@box[bg-green-pp text-white rounded my-box-pad2 fragment](<p style="line-height:70%"><span style="font-size:0.9em" >Larger image because of debug code & embedded info<br>&nbsp;  </span></p>)
@box[bg-gold2 text-white rounded my-box-pad2  fragment](<p style="line-height:70%"><span style="font-size:0.9em" >Uses the serial port for debug string output<br>&nbsp; </span></p>)
@box[bg-royal text-white rounded my-box-pad2  fragment](<p style="line-height:80%"><span style="font-size:0.9em" >Contains detailed debug strings that show the<br> boot progress and various <font face="Consolas">ASSERT / TRACE</font> errors<br>&nbsp; </span></p>)

 
Note:

### DEBUG build …
- Contains detailed debug strings that show the boot process, along with various ASSERT/TRACE errors
- Uses the serial port for debug string output
- Larger image than RELEASE, due to the embedded debug info
- Slower boot than RELEASE, due to the time it takes to display the debug info


### RELEASE build …
- Does not contain the debug strings
- Does not use the serial port for debug output
- Smaller image than DEBUG
- Faster boot than DEBUG

---?image=/assets/images/slides/Slide28.JPG
@title[Build Process Completed]
<p align="right"><span class="gold" >@size[1.1em](<b>Build Process Completed</b>)</span></p>
<span style="font-size:0.8em" >@size[1.25em](<font color="yellow"> &#10106;</font>)&nbsp;&nbsp;Locate the build <font face="Consolas">.Cap</font> images</span>

@snap[south-west span-100  ]
<p style="line-height:60%" align="left"><span style="font-size:0.6em" >
The platform post build process will create capsule images to use with a capsule update process<br>
The script displays the location of the final .cap files
</span></p>
@snapend

Note:
- The EDK II build generates multiple firmware volumes, which are combined in the .BIN image
- typically the platform script will call a stitching process to combine all the images together in  post processing after the EDK II build

for the the MinnnowBoard Capsule files are created to use withthe CapsuleApp.efi application

The platform post build process will create capsule images from the multiple firmware volumes generated by the EDK II build process


---?image=/assets/images/slides/Slide29.JPG
@title[Flash onto the MinnowBoard MAX]
<p align="right"><span class="gold" >@size[1.1em](<b>Flashing the New Firmware</b>)</span></p>


@snap[north-west span-100 ]
<br>
<p style="line-height:20%" align="left"><span style="font-size:0.8em">
<br><br><br>@size[1.125em](<font color="yellow"> &#10107;</font>)
</span></p>
<p style="line-height:70%" align="left"><span style="font-size:0.75em">
Flash the binary image
</span></p>
<p style="line-height:40%" align="left"><span style="font-size:0.65em">1.&nbsp; Access Max .CAP files from build folder</span><br><br>
<span style="font-size:0.5em; font-family:Consolas;" >
&nbsp;&nbsp;&bull; . . ./Build/Vlv2TbltDevicePkgX64/Capsules/TestCert_X64_DEBUG_GCC5<br>
&nbsp;&nbsp;&bull; *.cap <br>
&nbsp;&nbsp;&bull; RELEASE  . . ./Capsules/TestCert_X64_RELEASE_GCC5
</span></p>
<p style="line-height:55%" align="left"><span style="font-size:0.65em">2. 
&nbsp; Copy .cap files to a USB Thumb drive<br>3.
&nbsp; Copy <font face="Consolas">CapsuleApp.efi</font> to a USB thumb drive<br>4.
&nbsp; Boot into the UEFI Shell  on Max then  type "<font face="Consolas">FS0:</font>"
<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@size[.8em](using "screen")&nbsp;&nbsp;
<span style="background-color: #000000; font-family:Consolas;">@size[.7em](&nbsp;&nbsp;bash$ screen /dev/ttyUSB0 115200&nbsp;&nbsp;&nbsp;)
</span>
</span></p>
@snapend



Note:

1. Access Max .CAP files from build folder
 - . . ./Build/Vlv2TbltDevicePkgX64/Capsules/TestCert_X64_DEBUG_VS2015x86
 - *.cap 
 - RELEASE	. . ./Capsules/TestCert_X64_DEBUG_VS2015x86
2. Copy .cap files to a USB Thumb drive
3. Copy CapsuleApp.efi to a USB thumb drive
4. Boot into the UEFI Shell  on Max then  type “FS0:”

using “screen”       bash$ screen /dev/ttyUSB0 115200

---?image=/assets/images/slides/Slide30.JPG
@title[Flash onto the MinnowBoard MAX 02]
<p align="right"><span class="gold" >@size[1.1em](<b>Flashing the New Firmware</b>)</span></p>

@snap[north-west span-100 ]
<br>
<p style="line-height:45%" align="left" ><span style="font-size:0.20em; font-family:Consolas;" >&nbsp;&nbsp;<br><br></span></p>
<br>
<br>
@box[bg-grey-05 text-white rounded my-box-pad2  ](<p style="line-height:20% "><span style="font-size:0.9em;" ><br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100 ]
<br>
<p style="line-height:20%" align="left"><span style="font-size:0.8em">
<br><br><br><br>@size[1.125em](<font color="yellow"> &#10107;</font>)
</span></p>
<p style="line-height:70%" align="left"><span style="font-size:0.75em">
Run CapsuleApp.efi utility with MinnowMax. . . cap file<br>
@size[.7em](&lpar;Note the "TAB" Key will fill out the command line for you &rpar;)
</span></p>
<p style="line-height:40%" align="left"><span style="font-size:0.5em; font-family:Consolas;" >
&nbsp;&nbsp;@color[#ffda00](FS0:\&gt;)CapsuleApp.efi MinnowMax.0.0.0.12.cap <br>
</span></p>
<p style="line-height:65%" align="left"><span style="font-size:0.65em">
System will start the Capsule update process<br>
There will be 2 reboots
</span></p>
@snapend




Note:
Run CapsuleApp.efi utility with MinnowMax. . . cap file
(Note the “TAB” Key will fill out the command line for you )

FS0:\> CapsuleApp.efi MinnowMax.0.0.0.12.cap 
 
System will start the Capsule update process
There will be 2 reboots


---?image=/assets/images/slides/Slide31.JPG
@title[Capsule Update with External Monitor]
<p align="right"><span class="gold" >@size[1.1em](<b>Capsule Update with External Monitor</b>)</span></p>

<p style="line-height:70%" align="left"><span style="font-size:0.75em">
Logo with a progress bar will display update process progress
</span></p>


Note:

If an external monitor is connected to the system under test 
the monitor will show a progress bar for the capsule update

---?image=/assets/images/slides/Slide32.JPG
@title[Verify after Firmware Update]
<p align="right"><span class="gold" >@size[1.1em](<b>Verify After Firmware Update</b>)</span></p>


@snap[north-west span-100 ]
<br>
<p style="line-height:20%" align="left"><span style="font-size:0.8em">
<br><br><br>@size[1.125em](<font color="yellow"> &#10108;</font>)
</span></p>
<p style="line-height:70%" align="left"><span style="font-size:0.75em">
Reboot and Verify
</span></p>

<p style="line-height:70%" align="left"><span style="font-size:0.7em">
&bull;&nbsp; Verify that the Firmware was updated by checking the Date <br>
&bull;&nbsp; At the shell prompt type "exit" &nbsp;&nbsp; 
<span style="background-color: #0d0d0d"><font face="Consolas">@size[.7em](&nbsp;&nbsp; @color[#ffda00](Shell&gt;) exit &nbsp;&nbsp;)</font></span><br>
&bull;&nbsp; The EDK II front page will show the BIOS ID with Date/time stamp
</span></p>
@snapend



Note:

- Verify that the Firmware was updated by checking the Date
- At the shell prompt type “exit”
- The EDK II front page will show the BIOS ID with Date/time stamp


---  
@title[Summary]
##### <p align="center"<span class="gold"   >Summary </span></p><br>
<span style="font-size:0.9em">Lab Setup and Build for Minnowboard Max/Turbot</span> <br>
<br>
<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp; Hardware Setup for Minnowboard Max/Turbot </span><br><br>
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp; Build a EDK II Platform using Minnowboard <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Max/Turbot </span> <br><br>
 
---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/questions.JPG =10x) 

---
@title[return to main]
<p align="center"><span class="gold"   >@size[1.2em](<b>Return to Main Training Page</b>)</span></p>
<br>
<br>
<br>
<br>
<br>
<p align="center"><span style="font-size:0.9em">Return to Training Table of contents for next presentation <a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">link</a></span></p>

@snap[north span-30 ]
<br>
<br>
<br>
<a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">
![trainingLogo](/assets/images/returnTrainingLogo.png)</a>
@snapend

---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)


---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2019, Intel Corporation. All rights reserved.
**/

```

