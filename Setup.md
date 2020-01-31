- `amplify init`
  - ? Enter a name for the project fuchsstatusstatic
  - ? Enter a name for the environment dev
  - ? Choose your default editor: Visual Studio Code
  - ? Choose the type of app that you're building javascript
  - ? What javascript framework are you using none
  - ? Source Directory Path: app
  - ? Distribution Directory Path: dist
  - ? Build Command: npm run-script build
  - ? Start Command: npm run-script start
  - ? Do you want to use an AWS profile? Yes
  - ? Please choose the profile you want to use default
- `amplify add hosting`
  - ? Select the environment setup: PROD (S3 with CloudFront using HTTPS)
  - ? hosting bucket name fuchsstatusstatic-20200131162325-hostingbucket
- `amplify publish`
  - Yes, this takes _some_ time... Better grap a cup of coffee (or tea, or both)
- Add public read permissions to hosting bucket
  - Obviously you need to do this, otherwise you get an AccessDenied...
  - Go to your hosting bucket policy page (somethong like: https://s3.console.aws.amazon.com/s3/buckets/fuchsstatusstatic-20200131162325-hostingbucket-dev/?region=eu-central-1&tab=permissions)
  - Add the following in the bucket policy editor (replace the resource url with the correct one):
  ```json
  {
    "Sid": "PublicReadGetObject",
    "Effect": "Allow",
    "Principal": "*",
    "Action": ["s3:GetObject"],
    "Resource": "arn:aws:s3:::fuchsstatusstatic-20200131162325-hostingbucket-dev/*"
  }
  ```
  - click on save, done