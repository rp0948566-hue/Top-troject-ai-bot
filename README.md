# GitHub Activity Bot

This repository demonstrates a simple automation project using GitHub Actions to simulate activity by updating a log file at regular intervals.

<!-- Added a comment for demonstration -->

## Purpose

The goal of this project is to learn and experiment with GitHub Actions, automation, and CI/CD concepts. It creates a scheduled bot that updates an activity log file, commits the changes, and pushes them back to the repository.

**Warning:** This is for educational purposes only. It is not a substitute for real development activity and should not be used to artificially inflate contribution graphs.

## How It Works

The automation is handled by a GitHub Actions workflow located in `.github/workflows/activity-bot.yml`. The workflow:

1. Runs automatically every 15 minutes (configurable via cron schedule)
2. Checks out the repository
3. Appends a timestamp to `activity-log.txt`
4. Commits and pushes the changes if there are any

## Workflow Details

- **Trigger:** Scheduled every 15 minutes (`*/15 * * * *`) or manually via `workflow_dispatch`
- **Permissions:** Requires `contents: write` to push changes
- **Bot Identity:** Uses "activity-bot" as the commit author to avoid linking to real users
- **Conflict Handling:** The workflow checks for changes before committing to avoid empty commits
- **Authentication:** Uses the built-in `GITHUB_TOKEN` for pushing

## Files

- `activity-log.txt`: The file that gets updated with timestamps
- `.github/workflows/activity-bot.yml`: The GitHub Actions workflow configuration
- `README.md`: This documentation

## Timestamps

Timestamps are generated using the `date` command in the workflow runner (Ubuntu). The format is the default output of `date`, which includes date and time.

Example entry:
```
Updated: Mon Oct 16 14:30:00 UTC 2023
```

## Editing the Schedule

To change the frequency or disable the automation:

1. Open `.github/workflows/activity-bot.yml`
2. Modify the `cron` value under `schedule` (use [crontab.guru](https://crontab.guru/) for help)
3. To disable, comment out or remove the `schedule` section

## Manual Trigger

You can trigger the workflow manually from the Actions tab in GitHub, or by dispatching it via API.

## Setup

After pushing these files to your repository, the automation will start on the next scheduled run. The workflow must be enabled in the repository settings if it's disabled by default.
