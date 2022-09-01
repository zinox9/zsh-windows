# Installing ZSH on Windows 

### This readme is to help you install zsh on windows , for step by step method with images visit [My Dev.to Post](https://dev.to/zinox9/installing-zsh-on-windows-37em)

- You can refer the resources folder for some useful files

### 1. Cygwin Setup :

1. Download [Cygwin](https://cygwin.com/install.html)
2. When Running The Installer, Follow the Instructions. 
   1. Make Sure to Let the installer install at C:\cygwin64
   2. For Download site Select Any URL , Click Add
   3. **Stop** at packages screen, search **wget** expand **All** under **Web** select latest version of it under **bin** of **wget** no need to select Source. Then Continue. 
3. Finish Installing and launch the Terminal.  

- We are going to use Cygwin to Install Some Packages that will help to use Linux System on Windows. We will install **apt-cyg** which will work like apt-get and many other packages too like vim

4. Run The following to download apt-cyg with wget. Note you can prompt to  install gdb, vim or dos2unix if you want to use them or just remove them, you can install even more packages of your choice if you wish !

   
   ```cmd
     > wget rawgit.com/transcode-open/apt-cyg/master/apt-cyg
   ```
   ```cmd
     > install apt-cyg /bin
   ```
   ```cmd
     > apt-cyg install zsh git gdb dos2unix openssh vim [or your favorite text editor]
   ```
   
5. If you want your home folder to be your user's folder, you need to edit **cygwin64/etc/nsswitch.conf**.  You can do this in the text editor you just downloaded, or type `explorer /etc` to open the root directory to edit the file.
6. Add this line to the bottom: ```db_home: windows```

That's it for Cygwin , you can close the Terminal. Now let's move to the terminal we are using in this guide.

---

## 2. CMDER setup

1. Download and install one font from the package of [Powerline Font](https://github.com/powerline/fonts) to use in the terminal for the custom Icons. For This Guide I will be using **MesloGS NF** given in the Files of this Repo

2. [Download Cmder](https://cmder.app/) (the full Version !) it's a portable package so to install it just extract it into a folder where it can stay permanently.

3. Run cmder.exe

4. Right Click the Tab Bar and open Settings, We will be tweaking some of it. You Can Tweak As You Wish Too ! Or you can simply import my settings , file is in the resources folder.

      **i.** Under **General>Fonts.** = Select Main Console Font **MesloGS NF** and **remove check from Alternative Font**

      **ii.** Under **General>Size & Pos**. = Check Snap To desktop edges

      **iii.** Under **General>Appearance**. = 

      - You can remove Check from **Show Button In tab bar** and **Show Search Field** , 
      - check **Hide Scroll Bar**

      **iv.** Under **General>Tab bar** select **auto show**.

      **v.** Under **General>Confirm** You can switch off confirmation of creating new tab if you don't need it (I Never wanted it).

      **vi.** Under **General>Taskbar ** 

      - check **Don't show ConEmu Window on taskbar** & 
      - **Auto Minimize to TSA** (to not interrupt in alt+tab)

      **vii.** **IMPORTANT :**  Under **Startup>Tasks** 

      - Click on ``+`` then Rename it from ``Group xx`` to ``cygwin:ZSH``. 

      - Check **Default Task For New Console** 

      - Under Task you can give Location of any Icon You Wish to have (.ico file), icon available in resources

        ```-icon "C:\cygwin64\Cygwin.ico" ```

      - Now In the Last Command Box paste this command

        ```cmd
          C:\cygwin64\bin\mintty.exe /usr/bin/zsh --login -i -new_console:d:%USERPROFILE%
        ```

      - Last step is Click on **General** and choose startup task from the dropdown **{cygwin:ZSH}**

      - Do the same for Admin Privileges , rename it as **{cygwin:ZSH as Admin}** and replace command with 

        ```cmd
          *C:\cygwin64\bin\mintty.exe /usr/bin/zsh --login -i -new_console:d:%USERPROFILE%
        ```

      **viii.** Under **Features>Colors** choose **Monokai** Scheme

      **ix.** For the setup of shortcuts, Click on **Keys & Macro** then change the shortcuts. Here is my setup :

        ```cmd
          Win + Esc : MInimize/Restore
          Win + Down : Create New Console
          Win + T : Create new console (With Dialog)
          Win + N : Split: Duplicate active ‘shell’ split to bottom
          Win + Right : Switch Next Console 
          Win + Left : Switch Previous Console
          Win + Q : Close active Console
          Win + E : Close all Consoles
          Win + Alt + P : Show Settings 
          Win + Alt + Space : Show ConEmu Menu 
        ```
      - To make These Work go to **Keys & Macro>Keyboard** and check **Support Special Keys** 

      **x.** Under **Keys & Macro>Paste** make sure Multi Lines is Checked Everywhere. 

      **xi.**  After **Completing** the Settings Click On **Save Settings**. 

5. You Have setup to use Cygwin in Cmder, Close the terminal and open a new one 

6. Tada! you will see some differences, There You Go Running Cygwin In Cmder Successfully.

7. If a Prompt Comes type **0** to exit, we can edit the specified files later manually. 

---

## 3. Setting Up ZSH

Now let's add a manager to handle plugins, updating and themes. The Reason Why you are here 😉

1. Install **oh-my-zsh** the manual way, Run the lines one by one

  ```cmd
   > git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
   > cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
  ```

2. If it prompts , type **0** to exit

3. There You Go Running ZSH on WINDOWS !

---

#### Now we are going to theme and edit all features of zsh and cygwin you can continue if you wish to make it look like mine. 

---

## 4. Customization

- #### Changing Color Scheme and other Mintty settings

  1. Right click your terminal 
  2. Hit options

  3. Change font-size and Apply the settings , this creates **.minttyrc** file

  4. Browse to Root folder of the user , open **.minttyrc** file and paste my settings , file available in resources

  ```cmd
  BoldAsFont=no
  RightClickAction=paste
  Font=MesloLGS NF
  FontHeight=12
  Term=xterm-256color
  BoldAsColour=yes
  ConfirmExit=no
  Scrollbar=none
  Transparency=medium
  OpaqueWhenFocused=yes
  SelectionShowSize=1

  BackgroundColour=14,14,14
  ForegroundColour=228,228,228
  CursorColour=228,228,228
  Black=40,40,40
  BoldBlack=107,107,107
  Red=255,43,28
  BoldRed=243,91,80
  Green=2,192,97
  BoldGreen=0,253,127
  Yellow=251,188,46
  BoldYellow=253,197,86
  Blue=0,126,180
  BoldBlue=0,179,255
  Magenta=255,0,194
  BoldMagenta=239,133,214
  Cyan=87,208,249
  BoldCyan=141,219,245
  White=207,207,207
  BoldWhite=255,255,255
  ```



- <h3>Changing Zsh Themes and prompts</h3>
    - To install the **Powerlevel10k** theme that I am using you can run
    ```cmd
    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
    ```
    - Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`.
    - Close and Open a new terminal window
    - Finally Go through the setup in the prompt as you wish
    - I have edited the **p10k.zsh** file, manually to make it look even more clearner, the file is available in this repo

---
  - <h3>Adding Plugins</h3>
    - To install plugins just go to your root user folder, open `.zshrc` and you 
    will find a variable plugins. Simply add the plugins you want to install with 
    spaces `plugins=(git z zsh-autosuggestions)`
    - **Z** = saves the locations you visit the most, so that you can access it in one shot
    - **git** = brings many aliases in the command line
    - **npm Trash-cli** = it is an npm package, very useful to replace rm command
    - **Auto suggestions** = automatically suggests the code to type and autocomplete,  has to be installed manually not internally available 
      1. run `git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`
      2. add `zsh-autosuggestions` in plugins variable (available in resources)



### Setup Complete 🎉

---

## Extras

- You can checkout about all the features of oh-my-zsh on the internet , go explore
- Errors : 
  - on some commands oh-my-zsh ` runs less ` command with ` -R ` (repaint). You can disable this behavior by adding the following line **at the end** of your `~/.zshrc`

  ```cmd
    unset LESS;
  ```
  - This is set to `-R` in `~/.oh-my-zsh/lib/misc.zsh`

  - incase there is **Insecure completion-dependent directories** error : run this

  ```cmd
    chmod -R 755 ~/.oh-my-zsh
  ```
