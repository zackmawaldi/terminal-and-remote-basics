#### 1. **Introduction to the Terminal**

* **What is the Terminal?**

  * A text-based interface for interacting with the operating system.
* **Opening the Terminal**

  * macOS: Spotlight → Terminal
  * Linux: Ctrl + Alt + T
* **Basic Command Syntax**

  * Structure: `command --option argument`
  * Example: `cp -r old_folder new_folder`

---

#### 2. **Navigating the File System**

* **pwd (Print Working Directory)**

  * Show current directory.
* **ls (List)**

  * View contents of current directory.
* **cd (Change Directory)**

  * Move between directories.
* **mkdir (Make Directory)**

  * Create new folders.
* **Relative vs Absolute Paths**

  * Relative: `folder`, `./folder`, `~/folder`
  * Absolute: `/Users/zackmawaldi/folder`

---

#### 3. **File Operations**

* **touch**

  * Create an empty file.
* **cat, head, tail**

  * `cat`: Full file contents.
  * `head -n 10 file.txt`: First 10 lines.
  * `tail -n 10 file.txt`: Last 10 lines.
* **cp, mv, rm**

  * `cp`: Copy files/folders (`-r` for recursive).
  * `mv`: Move/rename files.
  * `rm`: Delete files/folders (`-r` for recursive).
    
* **man** for manual

---

#### 4. **Text Editing**

* **vim Basics**

  * `vim file.txt`: Open file.
  * Modes: Normal vs Insert (`i`, `Esc`).
  * Save: `:w`, Quit: `:q`, Save & Quit: `:wq`, Force quit: `:q!`

---

#### 5. **Piping and Redirection**

* **Pipe (`|`)**

  * Chain commands: `ls | grep txt`
* **Redirection**

  * `>`: Overwrite file: `ls > list.txt`
  * `>>`: Append to file: `echo "done" >> log.txt`

---

#### 6. **Scripting Basics**

* **Intro to Bash Scripts**

  * Automate terminal commands.
* **Create a Script**

  * Example: `hello.sh`

  ```bash
  #!/bin/bash
  echo "Hello World"
  ```

  * Make executable: `chmod +x hello.sh`
  * Run: `./hello.sh`

---

#### 7. **Advanced Bash Scripting**

* **Shebang**

  * Top line: `#!/bin/bash`
* **User Input**

  ```bash
  echo "What's your name?"
  read entered_name
  echo -e "\nWelcome to bash tutorial $entered_name"
  ```
* **Variables**

  ```bash
  country=USA
  same_country=$country
  ```
* **Positional Parameters**

  ```bash
  echo "First argument: $1"
  echo "Second argument: $2"
  ```
* **Reading Lines from a File**

  ```bash
  while read line; do
    echo $line
  done < myfile.txt
  ```
* **Conditional Statements**

  ```bash
  if [ $1 -lt 10 ]; then
    echo "Less than 10"
  elif [ $1 -gt 10 ]; then
    echo "Greater than 10"
  else
    echo "Equal to 10"
  fi
  ```

  * Operators:

    * `-lt` (less than), `-gt` (greater than)
    * `-a` (and), `-o` (or)
* **Loops**

  ```bash
  for i in {1..5}; do
    echo "Iteration $i"
  done
  ```

---

#### 8. **Introduction to HPC and SLURM**

* **SSH to Remote Server**

  ```bash
  ssh username@44.212.68.81
  ```
* **Create a SLURM Job Script (hello.sh)**

  ```bash
  #!/bin/bash
  #SBATCH --job-name=hello_job
  #SBATCH --output=output.out
  #SBATCH --ntasks=1
  #SBATCH --time=00:01:00
  #SBATCH --mem=100M

  sleep 60
  echo "Hello world after sleep!"
  ```
* **Make it Executable**

  ```bash
  chmod +x hello.sh
  ```
* **Submit Job**

  ```bash
  sbatch hello.sh
  ```
* **Monitor Job**

  ```bash
  squeue -u your_username
  ```
* **Check Output**

  * When done, check `output.txt`
* **Transfer Files Back to Local**

  ```bash
  scp username@44.212.68.81:/path/to/output.txt ./local_output.txt
  ```
* **screen**
  * Start a persistent session: `screen`
  * Cntrl + A then D to detach
  * `screen -ls` to see sessions
  * Resume with: `screen -r` (+ optionally name)
  * Cntrl + D to kill session, or just exit