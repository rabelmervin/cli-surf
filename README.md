<p align="center">
  <img src="./images/wave.png" height=100>
</p>

Surfs up!

cli-surf is a real time ocean data and forecasting service used in the command line.

Inspired by [wttr.in](https://github.com/chubin/wttr.in)

## Usage

Using your browser or command-line interface you can access the service.

```
$ curl localhost:8000

Location:  San Diego

      .-``'.
    .`   .`
_.-'     '._ 
        
UV index:  6.4
Wave Height:  3.9
Wave Direction:  238.0
Wave Period:  9.8

```

<p align="center">
    <img src="images/surf.gif" alt="cli-surf gif" style="width: 700px; height: auto;">
</p>


**Arguments**
| Argument    | Description|
| -------- | ------- |
| location / loc  | Specify the location of your forecast. Ex: `location=new_york_city` **or** `location=nyc`.    |
| forecast / fc  | Number of forecast days. Max = 7, default = 0  |
| hide_wave / hw | Hide the default wave art    |
| show_large_wave / slw   | Show the large wave art   | 
| hide_uv / huv    | Hide uv index   | 
| hide_height / hh    | Hide surf height   | 
| hide_direction / hdir    | Hide Swell direction    | 
| hide_period / hp  | Hide swell period    | 
| hide_location / hl    | Hide location   | 
| hide_date / hdate  | Hide date in forecast   | 
| metric / m  | Numbers in Metric units. Defaults to Imperial   | 
| decimal / dec   | Specify decimal points in output   | 
| color / c   | Choose color of wave art. Ex: `color=light_blue`   | 
| json / j   | Output the data in JSON format. Must be the only argument  | 

**Examples**
* Arguments are seperated by commas.
* `curl localhost:8000`
* `curl localhost:8000?location=new_york,hide_height,hide_wave,show_large_wave`
* `curl localhost:8000?fc=3,hdate,loc=trestles`

**For detailed information you can access the [help](https://github.com/ryansurf/cli-surf/blob/main/help.txt) page**

* `curl localhost:8000/help`


## Installation

**Python Dependencies**
* python>=3.8.1
* geopy
* openmeteo_requests
* pandas
* python-dotenv
* Requests
* requests_cache
* retry_requests

To run locally on your machine, I recommend either:

**Using a [Python Virtual Environment](https://docs.python.org/3/library/venv.html)** 
1. `git clone https://github.com/ryansurf/cli-surf.git`
2. `cd cli-surf`
3. `mv .env.example .env`
4. `python3 -m venv venv`
5. `source venv/bin/activate`
6. `pip install -r requirements.txt`
7. `cd src/backend`
8. `python3 server.py`

**Or running Docker (install [Docker](https://docs.docker.com/engine/install/))**
1. `git clone https://github.com/ryansurf/cli-surf.git`
2. `cd cli-surf`
3. `mv .env.example .env`
4. `docker build -t cli-surf .`
5. `docker run -d -p 8000:8000 cli-surf`
    * Add `--restart unless-stopped` for automatic start on reboot

## Setup

**Variables**

Change `.env.example` to `.env`

| Variable    | Description|
| -------- | ------- | 
| `SMTP_SERVER`  | The email server you are using. Default = smtp.gmail.com |
| `EMAIL`  | The email you will send the report from. |
| `EMAIL_PW`  | The sending email's password |
| `EMAIL_RECEIVER`  | The email that will receive the report (your personal email) |
| `COMMAND`  | The command that will be ran and shown in the email. Default = `localhost:8000` |
| `SUBJECT`  | The email's subject. Default = Surf Report |

**config.json**

| Variable    | Description|
| -------- | ------- | 
| `port`  | The port you want to open to run the application. Default = `8000` |
| `ip_address`  | The ip your server is running on. Default = `localhost` |


**Email Server**

Optional, sends a surf report to a specified email.

You will need to setup an email account that is able to utilize SMTP services. I used Gmail, following Method #1 outlined [here](https://www.cubebackup.com/blog/how-to-use-google-smtp-service-to-send-emails-for-free/). After doing this, change the variables in `.env`

Execute by running `python3 send_email.py`. Running with cron is a good use case

**Frontend**

<p align="center">
    <img src="images/website.gif" alt="cli-surf_website gif" style="width: 700px; height: auto;">
</p>

Although this application was made with the cli in mind, there is a frontend.

`http://localhost:8000/home` **or** `<ip_of_host>:<port>/home` if the application is running on a different host or you have changed the default port.

You may need to change `ip_address` in `config.json` to match the ip of the host running the machine.

Now, running `python3 server.py` will launch the website!


## Contributing

Thank you for considering contributing to cli-surf!

See [CONTRIBUTING.md](https://github.com/ryansurf/cli-surf/blob/main/CONTRIBUTING.md) to get an idea of how contributions work.

Questions? Comments?

* [Discord](https://discord.gg/He2UpxRuJP)
* [Discussions](https://github.com/ryansurf/cli-surf/discussions)
* [GitHub](https://github.com/ryansurf)

## License
[![License](https://img.shields.io/:license-mit-blue.svg?style=flat-square)](https://badges.mit-license.org)