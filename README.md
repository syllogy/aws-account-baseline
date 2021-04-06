# AWS Account Baseline

Repository contains CloudFormation templates and scripts to setup a baseline AWS account.

## TL;DR

Steps to Deploy

1. Open your web browser and login to your AWS Account.
2. Click the button below to launch stack.
3. Fill out parameters

## CloudFormation Stacks

| Stack | Deploy Link |
| ----- | ------------- |
| Billing | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=baseline-billing-cur&templateURL=https://rolston-cloud-library.s3-us-west-2.amazonaws.com/aws-account-baseline/billing-cur.yml) |
| CloudTrail | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=baseline-cloudtrail-monitoring&templateURL=https://rolston-cloud-library.s3-us-west-2.amazonaws.com/aws-account-baseline/cloudtrail-monitoring.yml)|
| AWS Config | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=baseline-aws-config&templateURL=https://rolston-cloud-library.s3-us-west-2.amazonaws.com/aws-account-baseline/aws-config.yml) |
| IAM Password Policy | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=baseline-iam-password-policy&templateURL=https://rolston-cloud-library.s3-us-west-2.amazonaws.com/aws-account-baseline/iam-password-policy.yml) |

### AWS Config

The template configures CIS Level-1 compliant AWS Config resources for the AWS payer account

### Billing CUR

The template configures the Billing S3 bucket for the CUR files to meet CIS Level 1 benchmarks in the AWS payer account

### IAM Password Policy

The template configures CIS Level-1 compliant AWS Config resources for the AWS payer account

The following parameters are required in the deployment

| Parameter | Description | Default |
| --------- | ----------- | ------- |
| Max Password Age | Age of the password in days before expiration | 90 |
| Minimum Password Length | Minimum length required for password to be | 14 |
| Password History | Number of previous passwords to remember  | 24 |
| Require Lowercase Chars | Require at least one lowercase character  | true |
| Require Numbers | Require at least one number  | true |
| Require Symbols | Require at least one symbol  | true |
| Require Uppercase Chars | Require at least one uppercase character  | true |

## CloudShell Scripts

The scripts are designed to run in the AWS CloudShell.

### Delete All Default VPCs

> **Note:** This will delete **all** default VPCs in a new account

Run from the CloudShell in region to remove the default VPC. Script requires JQ to be installed.

```sh
curl -fsS https://raw.githubusercontent.com/grolston/aws-account-baseline/master/delete-default-vpc.sh | bash
```
